# Position Images: Inline, Anchored, and Fixed

## Goal

Control how images are placed in a document and how text flows around them
using `ImageInsertionMode` combinations.

## Source

- https://www.textcontrol.com/blog/2024/05/03/various-ways-of-inserting-images-into-tx-text-control/
- https://www.textcontrol.com/blog/2022/03/28/different-ways-to-insert-images/

## Insertion Modes Overview

The following modes are supported:

- `AsCharacter`
- `DisplaceCompleteLines`
- `DisplaceText`
- `AboveTheText`
- `BelowTheText`
- `MoveWithText`
- `FixedOnPage`

Possible mode combinations include:

- `DisplaceCompleteLines | MoveWithText`
- `DisplaceCompleteLines | FixedOnPage`
- `DisplaceText | MoveWithText`
- `DisplaceText | FixedOnPage`
- `AboveTheText | MoveWithText`
- `AboveTheText | FixedOnPage`
- `BelowTheText | MoveWithText`
- `BelowTheText | FixedOnPage`
- `AsCharacter`

## Anchored to Paragraph with Offset

```csharp
TXTextControl.Image image = new TXTextControl.Image("image.png", 4);

textControl1.Images.Add(image, new Point(500, 500), -1,
  TXTextControl.ImageInsertionMode.MoveWithText |
  TXTextControl.ImageInsertionMode.DisplaceText);
```

In this sample, the image is anchored to the paragraph at the current input
position with a `Point(500, 500)` twips offset.

## Inline Example (As Character)

```csharp
TXTextControl.Image myImage = new TXTextControl.Image();
myImage.Sizeable = false;
myImage.HorizontalScaling = 75;
myImage.VerticalScaling = 75;

textControl1.Images.Add(myImage, -1);
```

This inserts the image inline, so it behaves like a text character.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.imageinsertionmode.enumeration.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.imagecollection.add.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.image.class.htm
