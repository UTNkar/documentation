---
title: "Render Modes"
weight: 20
---

Two important files, `Bar.tsx` and `Kitchen.tsx`, in the front-end code contain almost all the user interfaces except for the statistics page.

Here's a quick overview of what each file includes:

- `Bar.tsx`: Contains the interfaces for the Bar, Delivery, History, and Waiter sections.
- `Kitchen.tsx`: Contains the interfaces for the Kitchen and Tap sections.

Initially, the system had only three interfaces: Bar, Kitchen, and Statistics. Due to changes brought about by the Covid-19 pandemic, there was a need for additional, slightly different versions of the Bar and Kitchen interfaces. For example, the Delivery interface is a modified version of one part of the Bar interface.

To avoid duplicating code, a technique called RenderModes was introduced in both `Bar.tsx` and `Kitchen.tsx`. This allows for easier updates and less repetition in the code.

RenderModes determine which components to display based on the properties, or props, provided when the components are used. You can see how this works in the `renderComponents()` function in `./frontend/src/components/App.tsx`. Check the code snippet below to see the implementation details.

{{% details "`renderComponents()`" %}}

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

{{% /details %}}

The implementation of render modes led to a more efficient structure: we now have a greater variety of interfaces while using fewer files. However, it might have been better to rename `Bar.tsx` and `Kitchen.tsx` to names that better reflect their broader purposes, such as `Ordering.tsx` and `Fulfilling.tsx`. This wasn't done, but it's a consideration for future updates.
