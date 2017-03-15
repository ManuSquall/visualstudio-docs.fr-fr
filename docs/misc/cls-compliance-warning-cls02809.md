---
title: "Avertissement de conformit&#233; CLS CLS02809 | Microsoft Docs"
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
  - "CLS02809"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02809"
ms.assetid: a6e7b8e5-1587-437e-9d07-8a32fc5c4842
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233; CLS CLS02809
Les propriétés adhéreront à un modèle d’attribution de nom spécifique  
  
 Les propriétés doivent adhérer à un modèle d’affectation de noms spécifique. Le nom des fonctions d’accesseur de la propriété doit être le même que le nom de la propriété, précédé de **get\_** ou de **set\_**.  
  
 L’attribut **specialname** doit être ignoré dans les comparaisons de noms et doit respecter les règles d’identificateur.  
  
 Pour plus d’informations sur la vérification de conformité CLS, consultez [CLS Compliant Assemblies](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 La déclaration de fonction suivante \(en langage d’assembly MSIL\) illustre ce qui peut provoquer l’avertissement CLS02809 :  
  
```  
.method public specialname instance void set_MyPropertya(int32 __unnamed000) cil managed { } // end of method One::set_MyProperty .method public specialname instance int32 get_MyPropertya() cil managed { } // end of method One::get_MyProperty .property instance int32 MyProperty() { .get instance int32 One::get_MyPropertya() .set instance void One::set_MyPropertya(int32) } // end of property One::MyProperty  
```  
  
 Notez que les noms des méthodes d’accesseur ne sont pas identiques au nom de la propriété.  Vous pouvez résoudre l’avertissement CLS02809 en garantissant que tous les noms de propriétés respectent le modèle d’affectation de noms.