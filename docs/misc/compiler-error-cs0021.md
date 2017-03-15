---
title: "Erreur du compilateur CS0021 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0021"
ms.assetid: 4eb5fa24-8261-4962-b36a-224be5074217
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0021
Impossible d’appliquer l’indexation à l’aide de \[\] à une expression de type 'type'  
  
 L’utilisateur a tenté d’accéder à une valeur via un indexeur dans un type de données qui ne prend pas en charge [Indexeurs](/dotnet/csharp/programming-guide/indexers/index).  
  
 L’erreur CS0021 peut se produire quand vous tentez d’utiliser un indexeur dans un assembly C\+\+. Dans ce cas, décorez la classe C\+\+ avec l’attribut `DefaultMember` pour que le compilateur C\# puisse connaître l’indexeur par défaut. L’exemple suivant génère l’erreur CS0021 :  
  
## Exemple  
 Ce fichier est compilé en un fichier .dll \(avec l’attribut `DefaultMember` commenté\), afin de générer l’erreur.  
  
```  
// CPP0021.cpp // compile with: /clr /LD using namespace System::Reflection; // Uncomment the following line to resolve //[DefaultMember("myItem")] public ref class MyClassMC { public: property int myItem[int] { int get(int i){  return 5; } void set(int i, int value) {} } };  
```  
  
## Exemple  
 Voici le fichier C\# qui appelle le fichier .dll. Ce fichier tente d’accéder à la classe via un indexeur, mais parce qu’aucun membre n’a été déclaré en tant qu’indexeur par défaut, l’erreur est générée.  
  
```  
// CS0021.cs // compile with: /reference:CPP0021.dll public class MyClass { public static void Main() { MyClassMC myMC = new MyClassMC(); int j = myMC[1]; // CS0021 } }  
```