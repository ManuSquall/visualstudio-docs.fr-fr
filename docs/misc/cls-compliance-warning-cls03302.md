---
title: "Avertissement de conformit&#233; CLS CLS03302 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS03302"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03302"
ms.assetid: 3b99e64b-d5cb-4eb8-81b5-fd96992f2c10
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233; CLS CLS03302
Les événements doivent adhérer à un modèle d’attribution de nom spécifique  
  
 Les événements doivent adhérer à un modèle d’affectation de noms spécifique. Le nom des fonctions d’accesseur de l’événement doit être le même que le nom de l’événement, précédé de **raise\_**, **remove\_** ou **add\_**.  
  
 L’attribut **specialname** doit être ignoré dans les comparaisons de noms et doit respecter les règles d’identificateur.  
  
 Pour plus d’informations sur la vérification de la conformité CLS, consultez [CLS Compliant Assemblies](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 La déclaration de fonction suivante \(en langage d’assembly MSIL\) montre ce qui peut provoquer l’erreur CLS03302 :  
  
```  
.method public specialname instance void add_MyEventaaa(class MyAssemblyDelegate __unnamed000) cil managed { } // end of method One::add_MyEvent .method public specialname instance void remove_MyEventaaa(class MyAssemblyDelegate __unnamed000) cil managed { } // end of method One::remove_MyEvent .method public specialname instance void raise_MyEventaaa(object __unnamed000, class [mscorlib]System.EventArgs __unnamed001) cil managed { } // end of method One::raise_MyEvent .event specialname MyAssemblyDelegate MyEvent { .addon instance void One::add_MyEventaaa(class MyAssemblyDelegate) .removeon instance void remove_MyEventaaa(class MyAssemblyDelegate) .fire instance void raise_MyEventaaa(object, class [mscorlib]System.EventArgs) } // end of event One::MyEvent } // end of class One  
```  
  
 Notez que les noms des méthodes d’accesseur ne sont pas identiques au nom de l’événement.  Vous pouvez résoudre l’avertissement CLS03302 en garantissant que tous les noms d’accesseur d’événement respectent le modèle d’affectation de noms.