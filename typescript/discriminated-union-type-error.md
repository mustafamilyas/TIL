# Discriminated Union Type Error

when our typing rely on discriminated union, we might face some errors. Here are several cause of them:

1. Duplicate discriminator
   when we implement discriminated union, usually we have an attribute that differentiate between each typing. For example:

   ```typescript
   interface Circle {
     type: ShapeType.CIRCLE;
     radius: number;
   }

   interface Rectangle {
     type: ShapeType.RECTANGLE;
     height: number;
     width: number;
   }

   interface Square {
     type: ShapeType.SQUARE;
     side: number;
   }

   type Shape = Circle | Rectangle | Square;
   ```

   At the code above, the discriminator is `type` attribute. We must assign **unique** discriminator. This is easy to see when we have a small set of discriminator, but as the codebase grows large, we might miss some duplicate discriminator. Take a look at code below.

   ```typescript
   export interface GeneralSurveyResponseContentProps
     extends BasicSurveyResponseContentProps {
     type:
       | QuestionType.TITLE
       | QuestionType.EMAIL
       | QuestionType.PHONE
       | QuestionType.SINGLE_TEXT
       | QuestionType.PARAGRAPH
       | QuestionType.MULTIPLE_CHOICE
       | QuestionType.FILE_UPLOAD // this is duplicate
       | QuestionType.DATE
       | QuestionType.NUMBER;
     value: Value[];
   }

   export interface FileUploadSurveyResponseContentProps
     extends BasicSurveyResponseContentProps {
     type: QuestionType.FILE_UPLOAD;
     value: ValueWithGroupedFileUploadTypes[];
   }
   ```

2. General discriminator
   Sometime we want to have a fallback type, especially when we want to have a general functionality for other unhandled type. We might do something like this.

   ```typescript
   interface Other {
     type: ShapeType;
   }

   interface Circle {
     type: ShapeType.CIRCLE;
     radius: number;
   }

   interface Rectangle {
     type: ShapeType.RECTANGLE;
     height: number;
     width: number;
   }

   interface Square {
     type: ShapeType.SQUARE;
     side: number;
   }

   type Shape = Circle | Rectangle | Square | Other;

   function getArea(shape: Shape) {
     switch (shape.type) {
       case ShapeType.CIRCLE:
         return getCircleArea(shape);
       case ShapeType.SQUARE:
         return getSquareArea(shape);
       case ShapeType.RECTANGLE:
         return getRectangleArea(shape);
       default:
         return 0;
     }
   }
   ```

   It will throw a warning

   ```
   Argument of type 'Circle | Other' is not assignable to parameter of type 'Circle'. Property 'radius' is missing in type 'Other' but required in type 'Circle'.
   ```

3. False checking
   ![](/typescript/assets/false-checking.png)
   Please check your conditional. This why we need to have a discriminator to make it easier to differentiate between "Shape"
