# react-shimmer-skeleton
A react library for generating custom skeleton loading components automatically

## Installing

You can install it using npm:
```
npm install react-shimmer-skeleton
```

or yarn: 
```
yarn add react-shimmer-skeleton
```

## Basic Usage 

Just pass the component you want to load as a children to the Skeleton component. 
If the children is receiving any props, you should also pass to the Skeleton component a 
`component` prop, which is the function of the children component
and an `exampleProps` prop, which is an object with the same props that your component receives, 
that will be used to determine, for example, the length of the texts.

Here is a basic example: 
```
import Skeleton from 'react-shimmer-skeleton'

import {UserCard} from '../Components/UserCard'

//This mimics a delay from the api
const [isLoading, setIsLoading] = useState(true)
useEffect(()=>{
  setTimeout(()=>{
    setIsLoading(false)
  },2000)
},[])

//imagine this data is coming from an api
const user = {
  name: 'Filipe Pfluck',
  avatar: 'https://avatars.githubusercontent.com/u/62773200?v=4',
  description: 'Fullstack developer focused in typescript.'
}

//Now let's create an example user:
const fakeUser = {
  name: 'Joe Doe',
  avatar: 'https://cdn.pixabay.com/photo/2015/10/05/22/37/blank-profile-picture-973460__340.png',
  description: 'Lorem ipsum dolor sit, amet consectetur adipisicing elit.'
}

...

return(
  <Skeleton
    isLoading={isLoading}
    component={UserCard}
    exampleProps={{user: fakeUser}}
  >
    <UserCard user={user}/>
  </Skeleton>
)
```

![GIF example](https://github.com/FilipePfluck/react-shimmer-skeleton/blob/main/skeleton3.gif)
