---
title: "Extract Interface Refactoring (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.extractinterface"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactoring [C#], Extract Interface"
  - "Extract Interface refactoring operation [C#]"
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Extract Interface Refactoring (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Extraire l'interface est une opération de refactorisation qui offre un moyen facile de créer une nouvelle interface avec des membres originaires d'une classe, struct ou interface existante.  
  
 Lorsque plusieurs clients utilisent le même sous\-ensemble de membres d'une classe, struct ou interface, ou lorsque plusieurs classes, structs ou interfaces ont en commun un sous\-ensemble de membres, il peut être utile d'incarner le sous\-ensemble de membres dans une interface.  Pour plus d'informations sur l'utilisation d'interfaces, consultez [Interfaces](/dotnet/csharp/programming-guide/interfaces/index).  
  
 Extraire l'interface génère une interface dans un nouveau fichier et positionne le curseur au début du nouveau fichier.  Vous pouvez spécifier les membres à extraire dans la nouvelle interface, le nom de la nouvelle interface et le nom du fichier généré à l'aide de la boîte de dialogue **Extraire l'interface**.  
  
### Pour utiliser Extraire l'interface  
  
1.  Créez une application console nommée `ExtractInterface`, puis remplacez `Program` par le code suivant  
  
    ```c#  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2.  Placez le curseur sur `MethodB` et cliquez sur **Extraire l'interface** dans le menu **Refactoriser**.  
  
     La boîte de dialogue **Extraire l'interface**s'affiche.  
  
     Vous pouvez également utiliser le raccourci clavier CTRL\+R, I pour afficher la boîte de dialogue **Extraire l'interface**.  
  
     Vous pouvez également cliquer avec le bouton droit, pointer sur **Refactoriser**, puis cliquer sur **Extraire l'interface** pour afficher la boîte de dialogue **Extraire l'interface**.  
  
3.  Cliquez sur **Sélectionner tout**.  
  
4.  Cliquez sur **OK**.  
  
     Vous découvrez le nouveau fichier, IProtoA.cs, et le code suivant :  
  
    ```c#  
    using System;  
    namespace TopThreeRefactorings  
    {  
        interface IProtoA  
        {  
            void MethodB(string s);  
        }  
    }  
    ```  
  
## Notes  
 Cette fonctionnalité est accessible uniquement lorsque le curseur est positionné dans la classe, struct ou interface qui contient les membres que vous voulez extraire.  Lorsque le curseur est dans cette position, appelez l'opération de refactorisation Extraire l'interface.  
  
 Lorsque vous appelez Extraire l'interface sur une classe ou sur une struct, la liste des bases et interfaces est modifiée pour refléter l'inclusion du nouveau nom d'interface.  Lorsque vous appelez Extraire l'interface sur une interface, la liste des bases et interfaces n'est pas modifiée.  
  
## Voir aussi  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)