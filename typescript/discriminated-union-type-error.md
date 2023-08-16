# Possible Error Causes When Creating Discriminated Union Type

when our typing relies on discriminated unions, we might face some errors. Here are several causes of them:

1. Duplicate discriminator
   When we implement discriminated union, usually we have an attribute that differentiates between each typing. For example:

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

   In the code above, the discriminator is the `type` attribute. We must assign a **unique** discriminator. This is easy to see when we have a small set of discriminators, but as the codebase grows large, we might miss some duplicate discriminators. Take a look at the code below.

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
       | QuestionType.FILE_UPLOAD //This is duplicate
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
   Sometimes we want to have a fallback type, especially when we want to have a general functionality for other unhandled types. We might do something like this.

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
