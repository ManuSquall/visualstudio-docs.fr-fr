---
title: "Reorder Parameters Refactoring (C#) | Microsoft Docs"
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
  - "vs.csharp.refactoring.reorder"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactoring [C#], Reorder Parameters"
  - "Reorder Parameters refactoring [C#]"
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Reorder Parameters Refactoring (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`Reorder Parameters` est une opération de refactorisation de Visual C\# qui offre un moyen facile de modifier l'ordre des paramètres pour les méthodes, les indexeurs et les délégués.  `Reorder Parameters` modifie la déclaration, et à tous les emplacements où le membre est appelé, les paramètres sont réorganisés pour refléter le nouvel ordre.  
  
 Pour exécuter l'opération `Reorder Parameters`, mettez le curseur sur ou en regard d'une méthode, d'un indexeur ou d'un délégué.  Lorsque le curseur est en position, appelez l'opération `Reorder Parameters` en appuyant sur le raccourci clavier, ou en cliquant sur la commande dans le menu contextuel.  
  
> [!NOTE]
>  Vous ne pouvez pas réorganiser le premier paramètre dans une méthode d'extension.  
  
### Pour réorganiser les paramètres  
  
1.  Créez une bibliothèque de classes nommée `ReorderParameters`, puis remplacez `Class1` par l'exemple de code suivant.  
  
    ```c#  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  Placez le curseur sur `MethodB`, soit dans la déclaration de méthode, soit dans l'appel de méthode.  
  
3.  Dans le menu **Refactoriser**, cliquez sur **Réorganiser les paramètres**.  
  
     La boîte de dialogue **Réorganiser les paramètres** s'affiche.  
  
4.  Dans la boîte de dialogue **Réorganiser les paramètres**, sélectionnez `int i` dans la liste **Paramètres**, puis cliquez sur le bouton de déroulement vers le bas.  
  
     Vous pouvez également faire glisser `int i` à la suite de `bool b` dans la liste **Paramètres**.  
  
5.  Dans la boîte de dialogue **Réorganiser les paramètres**, cliquez sur **OK**.  
  
     Si l'option **Afficher un aperçu des modifications de la référence** est sélectionnée dans la boîte de dialogue **Réorganiser les paramètres**, la boîte de dialogue **Afficher les modifications \- Réorganiser les paramètres** s'affiche.  Elle fournit un aperçu des modifications dans la liste de paramètres pour `MethodB` à la fois dans la signature et l'appel de méthode.  
  
    1.  Lorsque la boîte de dialogue **Afficher les modifications \- Réorganiser les paramètres** apparaît, cliquez sur **Appliquer**.  
  
         Dans cet exemple, la déclaration de méthode et tous les sites d'appel de méthode de `MethodB` sont mis à jour.  
  
## Notes  
 Vous pouvez réorganiser les paramètres à partir d'une déclaration ou d'un appel de méthode.  Positionnez le curseur sur \(ou en regard de celle\-ci\) la déclaration de méthode ou de délégué, mais pas dans le corps.  
  
## Voir aussi  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)