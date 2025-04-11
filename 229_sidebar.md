# Blazorise Sidebar component

The Sidebar component is an expandable and collapsible container area that holds primary and secondary information placed alongside the main content of a webpage.

The sidebar extension is defined of several different components:

- &lt; Sidebar&gt; main sidebar component
    - &lt; SidebarContent&gt; container for the sidebar brand and navigation
        - &lt;SidebarBrand&gt; brand logo or link located in the sidebar header
        - &lt; SidebarNavigation&gt; container for the sidebar navigation items
            - &lt;SidebarLabel&gt; simple label to separate navigation items
            - &lt; SidebarItem&gt; navigation item that holds the link or subitems
                - &lt;SidebarLink&gt; simple label to separate navigation items
                - &lt;SidebarSubItem&gt; simple label to separate navigation items

Please be aware that the sidebar component is obsolete and that is generally replaced by the newest  component.

## Installation

### NuGet

Install extension from NuGet.

```
Install-Package Blazorise.Sidebar
```

### Imports

In your main  add:

```
@using Blazorise.Sidebar
```

### Static files

Include CSS link into your  or  /  file, depending if you’re using a Blazor WebAssembly or Blazor Server side project.

```
<link href="_content/Blazorise.Sidebar/blazorise.sidebar.css" rel="stylesheet" />
```

### Usage

When defining a sidebar structure you can chose between manual or dynamic building. Please note that you cannot combine both of them so you have to chose the one that suits you best.

### Manual

When building your sidebar manually you have full control of it’s content and navigation item. You can combine every sidebar component as you wish.

- Main
- Home
- Email
    - Inbox
    - Compose Email
- Apps
    - Todo List

```
<Sidebar @ref="sidebar">
    <SidebarContent>
        <SidebarBrand>
            <a href="#">Blazorise Sidebar</a>
        </SidebarBrand>
        <SidebarNavigation>
            <SidebarLabel>Main</SidebarLabel>
            <SidebarItem>
                <SidebarLink To="#" Title="Home">
                    <Icon Name="IconName.Home" Margin="Margin.Is3.FromEnd" />Home
                </SidebarLink>
            </SidebarItem>
            <SidebarItem>
                <SidebarLink Toggled="(isOpen)=> mailSidebarSubItems.Toggle(isOpen)" IsShow>
                    <Icon Name="IconName.Mail" Margin="Margin.Is3.FromEnd" />Email
                </SidebarLink>
                <SidebarSubItem @ref="mailSidebarSubItems" IsShow>
                    <SidebarItem>
                        <SidebarLink To="#email/inbox">Inbox</SidebarLink>
                    </SidebarItem>
                    <SidebarItem>
                        <SidebarLink To="#email/compose">Compose Email</SidebarLink>
                    </SidebarItem>
                    @* other subitems *@
                </SidebarSubItem>
            </SidebarItem>
            <SidebarItem>
                <SidebarLink Toggled="(isOpen)=> appsSidebarSubItems.Toggle(isOpen)" IsShow>
                    <Icon Name="IconName.Smartphone" Margin="Margin.Is3.FromEnd" />Apps
                </SidebarLink>
                <SidebarSubItem @ref="appsSidebarSubItems" IsShow>
                    <SidebarItem>
                        <SidebarLink To="#apps/todo">Todo List</SidebarLink>
                    </SidebarItem>
                </SidebarSubItem>
            </SidebarItem>
        </SidebarNavigation>
    </SidebarContent>
</Sidebar>
```

```
@code{
    Sidebar sidebar;
    SidebarSubItem mailSidebarSubItems;
    SidebarSubItem appsSidebarSubItems;

    void ToggleSidebar()
    {
        sidebar.Toggle();
    }
}
```

### Dynamic

You can also build sidebar dynamically by using the  attribute and the  class. The  is fully serializable so you can save it to an external source or database.

- Dashboard
- Email
    - Inbox
    - Compose Email
- Applications
    - Todo List

```
<Sidebar Data="@sidebarInfo" />
```

```
@code{
    SidebarInfo sidebarInfo = new SidebarInfo
    {
        Brand = new SidebarBrandInfo
        {
            Text = "Blazorise Demo"
        },
        Items = new List<SidebarItemInfo>
    {
            new SidebarItemInfo { To = "#", Text = "Dashboard" },
            new SidebarItemInfo
            {
                Text = "Email",
                Icon = IconName.Mail,
                SubItems = new List<SidebarItemInfo>
            {
                    new SidebarItemInfo { To = "#email/inbox", Text = "Inbox" },
                    new SidebarItemInfo { To = "#email/compose", Text = "Compose Email" },
                }
            },
            new SidebarItemInfo
            {
                Text = "Applications",
                SubItems = new List<SidebarItemInfo>
            {
                    new SidebarItemInfo { To = "#apps/todo", Text = "Todo List" }
                }
            },
        }
    };
}
```

###### On this page

#### 

## 