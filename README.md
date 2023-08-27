# react-native-screens-swiper
Simple screens' swiper library with scrollable or static tab navigation. Fully supported on iOS and Android.
Simple screens' swiper library with scrollable or static tab navigation. Fully supported on iOS and Android.

Scrollable Pills	Static Pills
drawing	drawing
❕ Attention ❕
We working on the new version of swiper ! In new version we will make:

Fix all problems of our sticky header container with childrens to make it more looks like in instagram profile. 🔥
Cleanup and simplify huge part of components. 🔥
New animation for nav. 🔥
TypeScript support. 🔥
Big docs. update for better understanding and user experience.
💥 For now it is all ! But if you have any proposal about performance or improvements of this lib. just write to us. 💥

New version will be available shortly ⌚

Installation
expo: expo install react-native-screens-swiper
npm: npm i react-native-screens-swiper
yarn: yarn add react-native-screens-swiper

Basic usage
import Swiper from "react-native-screens-swiper";
import FirstScreen from "./FirstScreen";
import SecondScreen from "./SecondScreen";

export default function YourComponent() {
    /**
     * Create an array with your screens' data - title, component and additional props.
     * Title is a string to be put inside of pill.
     * Props is an object with additional data for a particular screen.
     * Component can be either React component, render function or JSX element.
     * If it is a component or function, it will receive above-mentioned props and additional 'index' props
     */
    const data = [
        {
            tabLabel: 'Valid component in form of JSX element',
            component: <FirstScreen/>,
        },
        {
            tabLabel: 'Valid component in form of React component',
            component: SecondScreen,
            props: {}, // (optional) additional props
        },
        {
            tabLabel: 'Valid component in form of render function',
            component: ({index, ...props}) => {
                return null;
            },
            props: {}, // (optional) additional props
        },
    ];

    return (
        <Swiper
            data={data}
            isStaticPills={true}
            style={styles}
            // FlatList props
        />
    );
}

// more about styling below
const styles = {};
Custom styling
export default function App() {
    return (
        <Swiper 
            data={data}
            style={styles}
        />
    );
}

const styles = {
    // [View] Pills container
    pillContainer: {},

    // [View] Static pills container
    staticPillsContainer: {},

    // [View] Button
    pillButton: {},

    // [View] Active button
    pillActive: {},
    
    // [Text] Button's text
    pillLabel: {},
    
    // [Text] Active button's text
    activeLabel: {},
    
    // [View] Border of active pill (:warning: opacity will override animation's opacity)
    borderActive: {},
    
    // [View] Overflow container for pills container
    pillsOverflow: {
       // Needed if you want to add only bottom shadow
       // Just add the shadow for pillContainer and here add the overflow: 'hidden', and height 
    }
};
Example for scrollable pills
const styles = {
    pillButton: {
        backgroundColor: 'white',
    },
    pillActive: {
        backgroundColor: 'yellow',
    },
    pillLabel: {
        color: 'gray',
    },
    activeLabel: {
        color: 'white',
    },
};
drawing
Example for static pills
const styles = {
    borderActive: {
        borderColor: 'pink',
    },
    pillLabel: {
        color: 'gray',
    },
    activeLabel: {
        color: '#ba2d65',
    },
};
drawing
Sticky header and children
You can use sticky header only when scrollableContainer={true} so you need to pass it first. And after adding stickyHeaderEnabled={true} and stickyHeaderIndex={1} you can see the magic !

<Swiper 
    data={Screens} 
    style={styles} 
    isStaticPills={true} 
    stickyHeaderEnabled={true}
    scrollableContainer={true}
    stickyHeaderIndex={1}
>
    <View
        style={{
          height: 350,
          backgroundColor: 'white',
        }}
    >
        // other childrens here

    </View>
</Swiper>
drawing
Props
Below are the props you can pass to the React Component.

Prop	Type	Default	Example	Description
data	array		[{component: 'your first screen component', tabLabel: 'first screen tabLabel'}, {component: 'your second screen component', tabLabel: 'second screen tabLabel'}]	Put array of screens with tab labels for displaying inside the component
isStaticPills	boolean	false	isStaticPills={true}	When you need static navigation without scroll
stickyHeaderEnabled	boolean	false	stickyHeaderEnabled={true}	Can used only with scrollableContainer={true}. Give header possibility to stick to top of the screen.
scrollableContainer	boolean	false	scrollableContainer={true}	Added scrollable container.
children	component		<Swiper><YourComponent/></Swiper>	You can add your own top component in swiper. For example profile info.
style	object		{pillContainer: {backgroundColor: 'black', height: 50}}	The styles object for styling the swiper details. More about styling in Custom styling step.
initialScrollIndex	int		initialScrollIndex={1}	Screen index which will be opened on first open.
stickyHeaderIndex	int		stickyHeaderIndex={1}	An index of child indices determining which children get docked to the top of the screen when scrolling.
