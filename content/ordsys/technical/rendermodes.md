+++
title = "Render modes"
date =  2021-07-08
weight = 20
+++
##### (AKA "where the f*** is the waiter view code")
Two files in the front end source code stand out, namely `./frontend/src/components/Bar/Bar.tsx` and `./frontend/src/components/Kitchen/Kitchen.tsx`. That's because these two files are home to all views but the statistics view.

| File        | Views                           |
| ----------- | ------------------------------- |
| Bar.tsx     | Bar, Delivery, History & Waiter |
| Kitchen.tsx | Kitchen & Tap                   |


Originally, the bar, kitchen and statistics views were the only three views available in the system. As the use cases changed thanks to Covid-19, however, the need for variations of the kitchen and bar views arose. The kitchen view required a similar but slightly different tap view, the bar view needed similar but slightly different waiter and delivery views, etcetera. Notice how the delivery view is essentially just the third orders column from the bar view.

Since these views were so similar to each other, RenderModes were implemented into the Bar.tsx and Kitchen.tsx file. This meant less code had to be repeated and made changing the design easier.

Render modes work by passing a React prop to the different files when rendering them (instead of rendering separate files). Depending on which props are passed to the Bar and Kitchen file, different components are rendered. The different render mode props can be seen passed to the two files in the *renderComponents()* function of `./frontend/src/components/App.tsx`. Expand the snippet below to see it.

{{%expand "renderComponents()"%}}
```typescript
// ...
return (
    <>
        <Route exact path="/" component={Home} />
        <Route
            path="/bar"
            render={props => <Bar {...props} renderMode={BarRenderMode.FULL} />}
        />
        <Route
            path="/delivery"
            render={props => <Bar {...props} renderMode={BarRenderMode.DELIVERY} />}
        />
        <Route
            path="/kitchen"
            render={props => <Kitchen {...props} renderMode={KitchenRenderMode.FOOD} />}
        />
        <Route
            path="/history"
            render={props => <Bar {...props} renderMode={BarRenderMode.HISTORY} />}
        />
        <Route path="/statistics" component={Statistics} />
        <Route
            path="/tap"
            render={props => <Kitchen {...props} renderMode={KitchenRenderMode.BEVERAGES} />}
        />
        <Route
            path="/waiter"
            render={props => <Bar {...props} renderMode={BarRenderMode.WAITER} />}
        />
    </>
);
// ...
```
{{% /expand %}}

The end result was more views with less files, although in the process of adding render modes, the files should probably have been renamed from Bar.tsx and Kitchen.tsx to Ordering.tsx and Fulfilling.tsx, or something similar. Oh well.