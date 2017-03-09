---
title: "Avertissement du compilateur (niveau&#160;1) CS1570 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1570"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1570"
ms.assetid: a121d5c4-8b90-4cda-af5b-6ba8f23b2b1e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS1570
Le commentaire XML sur 'construction' contient du code XML mal rédigé — 'raison'  
  
 Quand vous utilisez [\/doc](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option), tous les commentaires du code source doivent être au format XML. Les erreurs de balisage XML génèrent l’avertissement CS1570. Exemple :  
  
-   Si vous passez une chaîne à un **cref**, comme dans une balise [\<exception\>](../Topic/%3Cexception%3E%20\(C%23%20Programming%20Guide\).md), la chaîne doit être entourée de guillemets doubles.  
  
-   Si vous utilisez une balise, telle que [\<seealso\>](../Topic/%3Cseealso%3E%20\(C%23%20Programming%20Guide\).md), qui n’a pas de balise de fermeture, vous devez spécifier une barre oblique avant le crochet angulaire fermant.  
  
-   Si vous devez utiliser les symboles « supérieur à » et « inférieur à » dans le texte de description, vous devez les représenter ainsi : **&gt;** et **&lt;**.  
  
-   L’attribut de fichier ou de chemin d’une balise [\<include\>](../Topic/%3Cinclude%3E%20\(C%23%20Programming%20Guide\).md) était manquant ou incorrect.  
  
 L’exemple suivant génère l’erreur CS1570 :  
  
```  
// CS1570.cs // compile with: /W:1 namespace ns { // the following line generates CS1570 /// <summary> returns true if < 5 </summary> // try this instead // /// <summary> returns true if <5 </summary> public class MyClass { public static void Main () { } } }  
```