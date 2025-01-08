
### **Enums in TypeScript**

**Enums** (এনাম) হলো TypeScript-এর একটি বিশেষ ফিচার যা JavaScript-এ পাওয়া যায়নি। এটি একটি মানের সেটের মধ্যে একটি নির্দিষ্ট নাম দেওয়া কনস্ট্যান্টকে বর্ণনা করতে ব্যবহৃত হয়। এর মাধ্যমে আপনি একাধিক ভ্যালু দিয়ে একটি নামকরণযোগ্য মান তৈরি করতে পারেন।

এটি একটি "run-time" ফিচার, মানে এটা শুধুমাত্র কোড চলাকালীন (runtime) কাজ করে এবং JavaScript-এ এটি একেবারেই নতুন কিছু নয়। TypeScript এর আগে JavaScript-এ এমন কিছু ছিল না। TypeScript-এ এই ফিচারটি বিশেষভাবে সাহায্য করে যখন আমাদের কিছু নির্দিষ্ট ভ্যালু, যা শুধুমাত্র কিছু নির্দিষ্ট নামের মধ্যে থাকবে, সেটি প্রোগ্রামে ব্যবহার করতে হয়।

### **Enums এর ব্যাবহার:**

এনাম তৈরি করার জন্য `enum` কিওয়ার্ড ব্যবহার করা হয়।

#### **১. Basic Enum (বেসিক এনাম)**

```typescript
enum Direction {
  Up = 1,
  Down = 2,
  Left = 3,
  Right = 4
}

let move: Direction = Direction.Up;
console.log(move); // 1
```

এখানে `Direction` একটি এনাম যা চারটি ভ্যালু ধারণ করে: **Up, Down, Left, Right**। আমরা প্রতিটি এনাম সদস্যের জন্য একটি সংখ্যা দিয়েছি, যদিও TypeScript স্বয়ংক্রিয়ভাবে প্রতি সদস্যের জন্য একটি ভ্যালু অ্যাসাইন করে (যেমন: **Up = 0, Down = 1** ইত্যাদি)। তবে, আমরা এখানে নিজে ভ্যালু প্রদান করেছি।

এনাম এভাবে কাজ করে:
- **Up** এর মান ১, **Down** এর মান ২, **Left** এর মান ৩, এবং **Right** এর মান ৪।

---

#### **২. String Enums (স্ট্রিং এনাম)**

এনাম শুধু সংখ্যা নয়, স্ট্রিংও ধারণ করতে পারে। স্ট্রিং এনামের ক্ষেত্রে আপনি নিজেই স্ট্রিং ভ্যালু দিতে পারেন।

```typescript
enum Color {
  Red = "RED",
  Green = "GREEN",
  Blue = "BLUE"
}

let myColor: Color = Color.Green;
console.log(myColor); // GREEN
```

এখানে **`Color`** এনামে স্ট্রিং ভ্যালু দেওয়া হয়েছে। প্রতিটি এনাম সদস্য একটি নির্দিষ্ট স্ট্রিং মান ধারণ করে, যেমন: **Red = "RED"**, **Green = "GREEN"**, এবং **Blue = "BLUE"**।

---

#### **৩. Heterogeneous Enums (হেটারোজেনিয়াস এনাম)**

একই এনামে বিভিন্ন ধরনের ভ্যালু (স্ট্রিং এবং সংখ্যা) মিশিয়েও ব্যবহার করা সম্ভব।

```typescript
enum MixedEnum {
  No = 0,
  Yes = "YES"
}

let response: MixedEnum = MixedEnum.Yes;
console.log(response); // YES
```

এখানে **`MixedEnum`** এনামে **`No`** একটি সংখ্যা (0) এবং **`Yes`** একটি স্ট্রিং ("YES")।

---

#### **৪. Enum এর অটোমেটিক ভ্যালু অ্যাসাইনমেন্ট**

যদি আপনি মান প্রদান না করেন, TypeScript নিজেই ভ্যালু প্রদান করে দেয়। প্রথম এনাম সদস্যের মান স্বয়ংক্রিয়ভাবে ০ হবে, এবং পরবর্তী সদস্যগুলো তার পরবর্তী সংখ্যা হিসেবে পাবেন।

```typescript
enum Status {
  Active,
  Inactive,
  Pending
}

let myStatus: Status = Status.Pending;
console.log(myStatus); // 2
```

এখানে **`Status`** এনামের প্রথম সদস্য **`Active`** এর মান স্বয়ংক্রিয়ভাবে ০, পরবর্তী সদস্য **`Inactive`** এর মান ১ এবং **`Pending`** এর মান ২ হবে।

---

#### **৫. Accessing Enums (এনাম অ্যাক্সেস করা)**

এনাম সদস্যকে আপনি তার নাম দিয়ে অথবা তার মান দিয়ে অ্যাক্সেস করতে পারেন।

```typescript
enum Status {
  Active = "ACTIVE",
  Inactive = "INACTIVE",
  Pending = "PENDING"
}

let myStatus: Status = Status.Active;
console.log(myStatus); // ACTIVE

// Enum value থেকে Enum member access করা
let statusName = Status["Inactive"];
console.log(statusName); // INACTIVE
```

এখানে, **`Status.Active`** ব্যবহার করে আমরা **`ACTIVE`** মানটি পেয়েছি এবং **`Status["Inactive"]`** ব্যবহার করে **`INACTIVE`** সদস্যটিও অ্যাক্সেস করেছি।

---

#### **৬. Reverse Mapping (রিভার্স ম্যাপিং)**

TypeScript এনামস এ **reverse mapping** সাপোর্ট করে, মানে আপনি যদি একটি এনাম সদস্যের মান জানেন, তবে আপনি তার সদস্যের নামও পেতে পারেন।

```typescript
enum Direction {
  Up = 1,
  Down,
  Left,
  Right
}

console.log(Direction[1]); // Up
console.log(Direction[2]); // Down
```

এখানে **`Direction[1]`** এর মাধ্যমে আমরা **`Up`** সদস্যটি পেয়ে গেছি, এবং **`Direction[2]`** এর মাধ্যমে **`Down`**।

---

### **কেন Enums ব্যবহার করবেন?**

**1. কোড পরিষ্কার ও বুঝতে সহজ:**  
   এনাম ব্যবহার করার মাধ্যমে আপনি সহজেই একাধিক কনস্ট্যান্টের মধ্যে নির্বাচন করতে পারেন। এটি কোডকে পরিষ্কার এবং মানানসই করে তোলে।

**2. টাইপ সেফটি:**  
   এনাম ব্যবহার করলে টাইপ সেফটি থাকে, যেমন আপনি একটি নির্দিষ্ট এনাম মান অ্যাসাইন করার চেষ্টা করলে, TypeScript ভুল টাইপের মান দিলে ত্রুটি দেখাবে।

**3. রিভার্স ম্যাপিং:**  
   এনাম আপনাকে **reverse mapping** এর সুবিধা দেয়, যেখানে আপনি কনস্ট্যান্ট মান দিয়ে তার সদস্য অ্যাক্সেস করতে পারেন।

---

### **এনাম ব্যবহার করে একটি প্রোজেক্টের উদাহরণ:**

ধরা যাক, আপনি একটি লাইব্রেরির স্ট্যাটাস ট্র্যাকিং ব্যবস্থা তৈরি করছেন। এখানে **`Status`** নামে একটি এনাম তৈরি করবেন, যাতে লাইব্রেরির স্ট্যাটাস ট্র্যাক করা হবে। এনামটি চারটি স্ট্যাটাস দেখাবে: **Active, Inactive, Archived, Pending**।

```typescript
enum Status {
  Active = "ACTIVE",
  Inactive = "INACTIVE",
  Archived = "ARCHIVED",
  Pending = "PENDING"
}

function getLibraryStatus(status: Status): string {
  switch (status) {
    case Status.Active:
      return "The library is currently active.";
    case Status.Inactive:
      return "The library is currently inactive.";
    case Status.Archived:
      return "The library has been archived.";
    case Status.Pending:
      return "The library status is pending.";
    default:
      return "Unknown status.";
  }
}

let currentStatus: Status = Status.Active;
console.log(getLibraryStatus(currentStatus)); // "The library is currently active."
```

এখানে, **`getLibraryStatus()`** ফাংশনে এনামটি ব্যবহার করা হয়েছে যাতে লাইব্রেরির স্ট্যাটাস সঠিকভাবে রিটার্ন করা যায়।

---



- **Enums** TypeScript এর একটি শক্তিশালী ফিচার যা একাধিক নির্দিষ্ট কনস্ট্যান্ট ভ্যালু নির্দিষ্ট নাম দিয়ে সংজ্ঞায়িত করতে সাহায্য করে।
- এটি **numbers**, **strings**, বা **mixed types** (স্ট্রিং এবং সংখ্যা মিশ্রিত) হিসেবে হতে পারে।
- **Reverse mapping** এবং **type safety** এনামকে আরও কার্যকরী ও সুবিধাজনক করে তোলে।

এটি বড় প্রকল্পে কোডের আড়ালে থাকা অর্থকে স্পষ্ট করতে এবং ডিবাগিং ও ট্র্যাকিং সহজ করতে সাহায্য করে।

----------------------------------------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------------------------------------






----------------------------------------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------------------------------------
