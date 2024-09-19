[logo]: https://raw.githubusercontent.com/Geeksltd/Zebble.Grid/master/icon.png "Zebble.Grid"


## Zebble.Grid

![logo]

A Zebble plugin that allow you to make grid in Zebble applications.


[![NuGet](https://img.shields.io/nuget/v/Zebble.Grid.svg?label=NuGet)](https://www.nuget.org/packages/Zebble.Grid/)

> A Grid is similar to ListView but instead of a single column it allows you to set the Columns (int) property.

<br>


### Setup
* Available on NuGet: [https://www.nuget.org/packages/Zebble.Grid/](https://www.nuget.org/packages/Zebble.Grid/)
* Install in your platform client projects.
* Available for iOS, Android and Windows.
<br>


### Api Usage

The items in the data source will be rendered using the provided Template class. Each row will be filled first before moving to the next row.

When you add a child to a Grid, it will be added to its "current horizontal stack", until there are as many items in it as the "Columns" of the grid. Once reached, if you try to add another child view, it will first create a new row and then add the child to that row.

A grid is essentially a vertical stack of horizontal stacks.

The child objects within the grid can be anything. Also the width of each object can be different. In that sense the Zebble Grid is different from a HTML table.

```xml
<Grid Id="MyGrid" Width="200" Height="250" Columns="2">
       <TextView Text="Row 1, left cell" />
       <TextView Text="Row 1, right cell" />
       <TextView Text="Row 2, left cell" />
       <TextView Text="Row 2, right cell" />
       <TextView Text="Row 3, left cell" />
       <TextView Text="Row 3, right cell" />
       ...
</Grid>
```

#### Ensure full columns
If the number of items in the last row is less than the columns, it adds empty canvas cells to fill it up. This is useful for when you want to benefit from the automatic width allocation.
```csharp
MyGrid.EnsureFullColumns();
```
#### Grid<TSource, TCellTemplate>
Just like ListView, Grid also comes in a generic form that is suitable for data binding scenarios. You can specify a data source and also an item templte so it can create the items for you automatically.

### Properties
| Property     | Type         | Android | iOS | Windows |
| :----------- | :----------- | :------ | :-- | :------ |
| Columns            | int           | x       | x   | x       |
| ExactColumns            | bool           | x       | x   | x       |
| DataSource | List<TSource&gt;           | x       | x   | x       |

### Events
| Event             | Type                                          | Android | iOS | Windows |
| :-----------      | :-----------                                  | :------ | :-- | :------ |
| EmptyTemplateChanged               | AsyncEvent    | x       | x   | x       |
| Searching              | AsyncEvent    | x       | x   | x       |

### Methods
| Method       | Return Type  | Parameters                          | Android | iOS | Windows |
| :----------- | :----------- | :-----------                        | :------ | :-- | :------ |
| UpdateSource         | Task| source -> IEnumerable<TSource&gt; | x       | x   | x       |