# Blazorise Pagination component

A responsive, usable, and flexible pagination.

The &lt;Pagination&gt; component enables the user to select a specific page from a range of pages.

- &lt; Pagination&gt; the main container.
- &lt;Pagination&gt; the main container.
    - &lt; PaginationItem&gt; the pagination item, which can be active or not.
    - &lt;PaginationItem&gt; the pagination item, which can be active or not.
        - &lt;PaginationLink&gt; the link to the destination page, which will trigger the &lt;Clicked&gt; event.

## Examples

### Basic

- «
- 1
- 2
- 3
- »

```
<Pagination>
    <PaginationItem Disabled="@isActive.First()" @onclick="Previous">
        <PaginationLink>
            <span aria-hidden="true">«</span>
        </PaginationLink>
    </PaginationItem>
    <PaginationItem Active="@isActive[0]">
        <PaginationLink Page="1" Clicked="SetActive">
            1
        </PaginationLink>
    </PaginationItem>
    <PaginationItem Active="@isActive[1]">
        <PaginationLink Page="2" Clicked="SetActive">
            2
        </PaginationLink>
    </PaginationItem>
    <PaginationItem Active="@isActive[2]">
        <PaginationLink Page="3" Clicked="SetActive">
            3
        </PaginationLink>
    </PaginationItem>
    <PaginationItem Disabled="@isActive.Last()" @onclick="Next">
        <PaginationLink>
            <span aria-hidden="true">»</span>
        </PaginationLink>
    </PaginationItem>
</Pagination>
```

```
@code
{
    private bool[] isActive = { false, true, false };

    private void Previous()
    {
        if (isActive[0])
            return;

        if (isActive[1])
        {
            SetActive("1");
            return;
        }

        if (isActive[2])
        {
            SetActive("2");
            return;
        }
    }

    private void Next()
    {
        if (isActive[0])
        {
            SetActive("2");
            return;
        }

        if (isActive[1])
        {
            SetActive("3");
            return;
        }

        if (isActive[2])
        {
            return;
        }
    }

    private void SetActive(string idx)
    {
        switch (idx)
        {
            case "1":
                isActive[0] = true;
                isActive[1] = false;
                isActive[2] = false;
                break;
            case "2":
                isActive[0] = false;
                isActive[1] = true;
                isActive[2] = false;
                break;
            case "3":
                isActive[0] = false;
                isActive[1] = false;
                isActive[2] = true;
                break;
            default:
                break;
        }

    }
}
```

### Dynamic

- «
- 1
- 2
- 3
- 4
- 5
- »

```
<Pagination>
    <PaginationItem Disabled="@IsPageNavigationDisabled(PREVIOUS)" @onclick="Previous">
        <PaginationLink>
            <span aria-hidden="true">«</span>
        </PaginationLink>
    </PaginationItem>
    @{
        for (var i = 1; i <= pageItems; i++)
        {
            var pageNumberAsString = i.ToString();
            <PaginationItem @key="pageNumberAsString" Active="@IsActive(pageNumberAsString)">
                <PaginationLink Page="@pageNumberAsString" Clicked="SetActive">
                    @pageNumberAsString
                </PaginationLink>
            </PaginationItem>
        } 
    }
    <PaginationItem Disabled="@IsPageNavigationDisabled(NEXT)" @onclick="Next">
        <PaginationLink>
            <span aria-hidden="true">»</span>
        </PaginationLink>
    </PaginationItem>
</Pagination>
```

```
@code
{
    private const string PREVIOUS = "previous";
    private const string NEXT = "next";
    private string currentPage = "2";
    private int pageItems = 5;

    private bool IsActive(string page)
        => currentPage == page;

    private bool IsPageNavigationDisabled(string navigation )
    {
        if (navigation.Equals(PREVIOUS))
        {
            return currentPage.Equals("1");
        }
        else if (navigation.Equals(NEXT))
        {
            return currentPage.Equals(pageItems.ToString());
        }
        return false;
    }

    private void Previous()
    {
        var currentPageAsInt = int.Parse(currentPage);
        if (currentPageAsInt > 1 )
        {
            currentPage = (currentPageAsInt - 1).ToString();
        }
    }

    private void Next()
    {
        var currentPageAsInt = int.Parse(currentPage);
        if (currentPageAsInt < pageItems )
        {
            currentPage = (currentPageAsInt + 1).ToString();
        }
    }

    private void SetActive(string page)
        => currentPage = page;
}
```

## API

### Parameters

#### Pagination

| Parameter    | Description                                                                       | Type           | Default           |
|--------------|-----------------------------------------------------------------------------------|----------------|-------------------|
| Alignment    | Gets or sets the pagination alignment.Possible values:Default, Start, Center, End | Alignment      | Alignment.Default |
| ChildContent | Specifies the content to be rendered inside this Pagination.                      | RenderFragment | null              |
| Size         | Gets or sets the pagination size.                                                 | Size?          | null              |

#### PaginationItem

| Parameter    | Description                                                      | Type           | Default   |
|--------------|------------------------------------------------------------------|----------------|-----------|
| Active       | Indicate the currently active page.                              | bool           | false     |
| ChildContent | Specifies the content to be rendered inside this PaginationItem. | RenderFragment | null      |
| Disabled     | Used for links that appear un-clickable.                         | bool           | false     |

#### PaginationLink

| Parameter    | Description                                                      | Type           | Default   |
|--------------|------------------------------------------------------------------|----------------|-----------|
| ChildContent | Specifies the content to be rendered inside this PaginationLink. | RenderFragment | null      |
| Page         | Gets or sets the page name.                                      | string         |           |

### Events

#### PaginationLink

| Event   | Description                           | Type                  |
|---------|---------------------------------------|-----------------------|
| Clicked | Occurs when the item link is clicked. | EventCallback<string> |

###### On this page

#### 

## 