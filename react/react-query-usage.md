# React Query Usage

React Query is a powerful library for managing server-state in React applications. It simplifies data fetching, caching, synchronization, and more.

## Installation

To install React Query, use the following command:

```bash
npm install react-query
```

or with yarn:

```bash
yarn add react-query
```

## Basic Usage

### Setting Up the Query Client

First, you need to set up the Query Client and provide it to your application:

```jsx
import { QueryClient, QueryClientProvider } from 'react-query';

const queryClient = new QueryClient();

function App() {
    return (
        <QueryClientProvider client={queryClient}>
            <YourComponent />
        </QueryClientProvider>
    );
}
```

### Fetching Data

To fetch data, use the `useQuery` hook:

```jsx
import { useQuery } from 'react-query';
import axios from 'axios';

const fetchUser = async () => {
    const { data } = await axios.get('/api/user');
    return data;
};

function User() {
    const { data, error, isLoading } = useQuery('user', fetchUser);

    if (isLoading) return <div>Loading...</div>;
    if (error) return <div>Error: {error.message}</div>;

    return (
        <div>
            <h1>{data.name}</h1>
            <p>{data.email}</p>
        </div>
    );
}
```

### Mutations

For creating, updating, or deleting data, use the `useMutation` hook:

```jsx
import { useMutation, useQueryClient } from 'react-query';
import axios from 'axios';

const addUser = async (newUser) => {
    const { data } = await axios.post('/api/user', newUser);
    return data;
};

function AddUser() {
    const queryClient = useQueryClient();
    const mutation = useMutation(addUser, {
        onSuccess: () => {
            queryClient.invalidateQueries('users');
        },
    });

    const handleSubmit = (event) => {
        event.preventDefault();
        const formData = new FormData(event.target);
        const newUser = Object.fromEntries(formData.entries());
        mutation.mutate(newUser);
    };

    return (
        <form onSubmit={handleSubmit}>
            <input name="name" placeholder="Name" required />
            <input name="email" placeholder="Email" required />
            <button type="submit">Add User</button>
        </form>
    );
}
```

## Conclusion

React Query simplifies data fetching and state management in React applications. By using hooks like `useQuery` and `useMutation`, you can easily manage server-state and keep your UI in sync with your backend.

For more advanced usage and features, refer to the [React Query documentation](https://react-query.tanstack.com/).
