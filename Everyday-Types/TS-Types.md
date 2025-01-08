###  ** Types (টাইপ)**

TypeScript-এ অনেক ধরনের ডেটা টাইপ (data types) রয়েছে, যা আপনি বিভিন্ন পরিস্থিতিতে ব্যবহার করতে পারেন। এখানে আমরা TypeScript-এর সব প্রধান টাইপগুলির একটি তালিকা এবং সংক্ষিপ্ত বিবরণ দেয়া হলো।

### ১. **Primitive Types (প্রাথমিক টাইপ)**
   - **`number`**: সংখ্যা (যেমন ১, ২, ৩.৫, -৭ ইত্যাদি)
   - **`string`**: টেক্সট মান (যেমন `"Hello"`, `"TypeScript"`)
   - **`boolean`**: দুইটি মান `true` অথবা `false`
   - **`null`**: একটি বিশেষ মান যা "কিছু নেই" বা "অনুপস্থিত"
   - **`undefined`**: একটি বিশেষ মান যা মান নির্ধারণ করা হয়নি
   - **`symbol`**: ইউনিক এবং অটোমেটিকলি তৈরি হওয়া একটি ভ্যালু, সাধারণত object property হিসেবে ব্যবহার হয়।
   - **`bigint`**: খুব বড় সংখ্যাগুলি স্টোর করার জন্য ব্যবহৃত হয়, যেগুলি `number` টাইপের বাইরে চলে যায় (যেমন 1n, 10n)

### ২. **Object Types (অবজেক্ট টাইপ)**
   - **`object`**: সাধারণ অবজেক্টের জন্য ব্যবহৃত টাইপ
   - **`Array`**: একটি অবজেক্ট যা একাধিক মান ধারণ করে
     - **Syntax**: `let numbers: number[] = [1, 2, 3];`
     - অথবা **Generic Syntax**: `let names: Array<string> = ["Alice", "Bob"];`
   - **`Tuple`**: একটি বিশেষ ধরনের অ্যারে যেখানে বিভিন্ন ধরনের ডেটা একসাথে থাকতে পারে
     - **Syntax**: `let person: [string, number] = ["Alice", 30];`
   - **`Enum`**: একটি সেটের মধ্যে নির্দিষ্ট মানের সংগ্রহ
     - **Syntax**: 
       ```typescript
       enum Color {
         Red,
         Green,
         Blue
       }
       let c: Color = Color.Green;
       ```

### ৩. **Special Types (বিশেষ টাইপ)**
   - **`any`**: যে কোনো ধরনের মান হতে পারে, তবে TypeScript-এ এটি একটি রিল্যাক্সড টাইপ হিসেবে গণ্য করা হয়। এই টাইপ ব্যবহারের ফলে আপনি TypeScript-এর সুবিধাগুলি হারান।
     - **Syntax**: `let something: any = "Hello";`
   - **`void`**: যে ফাংশন কোন মান ফেরত দেয় না, সেটি `void` টাইপের হবে।
     - **Syntax**: `function logMessage(message: string): void { console.log(message); }`
   - **`never`**: ফাংশন যখন কখনোই কোনো মান ফেরত দেয় না বা কোন কাজ শেষ করতে পারে না, তখন `never` টাইপ ব্যবহার হয়।
     - **Syntax**: `function throwError(message: string): never { throw new Error(message); }`

### ৪. **Union Types (ইউনিয়ন টাইপ)**
   - **`|`**: একাধিক টাইপের মধ্যে যেকোনো একটির মান হতে পারে
     - **Syntax**: `let value: string | number = "Hello";` অথবা `let value: string | number = 42;`
   - একাধিক টাইপের যেকোনো মান গ্রহণ করতে Union টাইপ ব্যবহার হয়।

### ৫. **Intersection Types (ইন্টারসেকশন টাইপ)**
   - **`&`**: একাধিক টাইপের সংমিশ্রণ
     - **Syntax**: `type Person = { name: string; } & { age: number; };`
   - Intersection টাইপ দুটি টাইপের সব বৈশিষ্ট্য একত্রিত করে।

### ৬. **Type Aliases (টাইপ অ্যালিয়াস)**
   - **`type`**: নতুন একটি টাইপ তৈরি করা যা পুরানো টাইপের সমতুল্য।
     - **Syntax**: 
       ```typescript
       type Point = { x: number; y: number };
       let pt: Point = { x: 10, y: 20 };
       ```

### ৭. **Literal Types (লিটারেল টাইপ)**
   - নির্দিষ্ট মান বা স্ট্রিং কেবলমাত্র নির্দিষ্ট মান গ্রহণ করবে।
   - **Syntax**: 
     ```typescript
     let direction: "left" | "right" = "left";
     ```

### ৮. **Function Types (ফাংশন টাইপ)**
   - ফাংশনের টাইপ নির্দিষ্ট করা
     - **Syntax**: 
       ```typescript
       let add: (a: number, b: number) => number = (a, b) => a + b;
       ```

### ৯. **Class Types (ক্লাস টাইপ)**
   - ক্লাসের টাইপ নির্দিষ্ট করা
     - **Syntax**: 
       ```typescript
       class Person {
         name: string;
         constructor(name: string) {
           this.name = name;
         }
       }

       let person: Person = new Person("Alice");
       ```

### ১০. **Type Assertions (টাইপ অ্যাসারশন)**
   - যখন আপনি নিশ্চিত যে একটি ভেরিয়েবলের একটি নির্দিষ্ট টাইপ হবে, তখন টাইপ অ্যাসারশন ব্যবহার করা হয়।
   - **Syntax**: 
     ```typescript
     let someValue: any = "Hello";
     let strLength: number = (someValue as string).length;
     ```

### ১১. **Nullable Types (ন্যুলেবল টাইপ)**
   - **`null`** এবং **`undefined`** মান কে সঠিকভাবে পরিচালনা করতে `null` এবং `undefined` টাইপের সাপোর্ট দেওয়া হয়।
   - **Syntax**: 
     ```typescript
     let name: string | null = null;
     ```

### ১২. **Readonly Types (রিড অনলি টাইপ)**
   - একটি ভেরিয়েবলকে পরিবর্তন করা থেকে আটকানোর জন্য `readonly` ব্যবহার করা হয়।
   - **Syntax**:
     ```typescript
     readonly array: number[] = [1, 2, 3];
     ```

### ১৩. **Constructor Types (কনস্ট্রাক্টর টাইপ)**
   - ফাংশন টাইপ যা একটি কনস্ট্রাক্টরের মতো কাজ করে।

---
