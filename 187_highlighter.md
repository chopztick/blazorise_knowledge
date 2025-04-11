# Blazorise Highlighter component

Visually highlight part of the text based on the search term.

Highlighter is Blazor component that changes format of wanted words and phrases, to make them more notable in text on web page (e.g. for database search results). You can change anything you can imagine, including font size, color, bold, italic, underline, background color etc., or simply use css styling.

## Examples

### Basic

- This is the first item
- This is the second item
- This is the third item

```
<Field>
    <FieldLabel>Search value</FieldLabel>
    <FieldBody>
        <TextEdit @bind-Text="@searchValue" />
    </FieldBody>
</Field>

<ListGroup>
    @foreach ( var sentence in sentences )
    {
        <ListGroupItem @key="sentence">
            <Highlighter Text="@sentence" HighlightedText="@searchValue" />
        </ListGroupItem>
    }
</ListGroup>
```

```
@code {
    string searchValue = "item";

    IEnumerable<string> sentences = new List<string>
    {
        "This is the first item",
        "This is the second item",
        "This is the third item"
    };
}
```

### Boundaries

If you wish to highlight the text until the next regex boundary occurs, set the  property to true, or the  property to true if you want a case-sensitive highlight.

"There will be no foolish wand-waving or sill incantations in this class. As such, I don't expect man of ou to appreciate the subtle science and exact art that is potion-making. However, for those select few who possess the predisposition, I can teach ou how to bewitch the mind and ensnare the senses. I can tell ou how to bottle fame, brew glor, and even put a stopper in death. Then again, mabe some of ou have come to Hogwarts in possession of abilities so formidable that ou feel confident enough to not pa attention!" — Severus Snape

```
<Fields>
    <Field>
        <FieldLabel>Search value</FieldLabel>
        <FieldBody>
            <TextEdit @bind-Text="@searchValue" />
        </FieldBody>
    </Field>
    <Field>
        <FieldLabel>Until Next Boundary</FieldLabel>
        <FieldBody>
            <Switch @bind-Checked="@untilNextBoundary"></Switch>
        </FieldBody>
    </Field>
    <Field>
        <FieldLabel>Case Sensitive</FieldLabel>
        <FieldBody>
            <Switch @bind-Checked="@caseSensitive"></Switch>
        </FieldBody>
    </Field>
</Fields>

<Card>
    <CardBody>
        <Highlighter Text="@sentence" HighlightedText="@searchValue" UntilNextBoundary="@untilNextBoundary" CaseSensitive="@caseSensitive" />
    </CardBody>
</Card>
```

```
@code {
    string searchValue = "y";
    bool untilNextBoundary;
    bool caseSensitive;

    string sentence = "\"There will be no foolish wand-waving or silly incantations in this class. As such, I don't expect many of you to appreciate the subtle science and exact art that is potion-making. However, for those select few who possess the predisposition, I can teach you how to bewitch the mind and ensnare the senses. I can tell you how to bottle fame, brew glory, and even put a stopper in death. Then again, maybe some of you have come to Hogwarts in possession of abilities so formidable that you feel confident enough to not pay attention!\" — Severus Snape";
}
```

## API

### Parameters

| Parameter         | Description                                                                | Type   | Default   |
|-------------------|----------------------------------------------------------------------------|--------|-----------|
| CaseSensitive     | Whether or not the search term will be case sensitive.                     | bool   | false     |
| HighlightedText   | The search term to be highlighted.                                         | string |           |
| NextBoundary      | A regex expression used for searching the word boundaries.                 | string | ".*?\\b"  |
| Text              | The whole text in which a Highlighter.HighlightedText will be highlighted. | string |           |
| UntilNextBoundary | If true, highlights the text until the next word boundary.                 | bool   | false     |

###### On this page

#### 

## 