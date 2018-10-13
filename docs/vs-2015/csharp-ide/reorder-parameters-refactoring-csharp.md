---
title: Réorganiser les paramètres (refactorisation c#) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 03316fba63267a4eb7fc3b59c8f6823d3678b438
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273102"
---
# <a name="reorder-parameters-refactoring-c"></a>Réorganisation de la refactorisation de paramètres (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Reorder Parameters` est un Visual c# opération de refactorisation qui offre un moyen facile pour modifier l’ordre des paramètres pour les méthodes, indexeurs et délégués. `Reorder Parameters` Modifie la déclaration, et à tous les emplacements où le membre est appelé, les paramètres sont réorganisés pour refléter le nouvel ordre.  
  
 Pour effectuer le `Reorder Parameters` opération, placez le curseur sur ou en regard d’une méthode, un indexeur ou un délégué. Lorsque le curseur est en position, appelez le `Reorder Parameters` opération en appuyant sur le raccourci clavier, ou en cliquant sur la commande dans le menu contextuel.  
  
> [!NOTE]
>  Vous ne pouvez pas modifier le premier paramètre dans une méthode d’extension.  
  
### <a name="to-reorder-parameters"></a>Pour réorganiser les paramètres  
  
1.  Créer une bibliothèque de classes nommée `ReorderParameters`, puis remplacez `Class1` avec l’exemple de code suivant.  
  
    ```csharp  
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
  
2.  Placez le curseur sur `MethodB`, soit dans la déclaration de méthode ou de l’appel de méthode.  
  
3.  Sur le **refactoriser** menu, cliquez sur **réorganiser les paramètres**.  
  
     Le **réorganiser les paramètres** boîte de dialogue s’affiche.  
  
4.  Dans le **réorganiser les paramètres** boîte de dialogue, sélectionnez `int i` dans le **paramètres** liste, puis cliquez sur le bouton bas.  
  
     Vous pouvez également faire glisser `int i` après `bool b` dans le **paramètres** liste.  
  
5.  Dans le **réorganiser les paramètres** boîte de dialogue, cliquez sur **OK**.  
  
     Si le **aperçu des modifications de référence** option est sélectionnée dans le **réorganiser les paramètres** boîte de dialogue, le **aperçu des modifications - Réorganiser les paramètres** boîte de dialogue s’affiche. Elle fournit un aperçu des modifications dans la liste de paramètres `MethodB` dans la signature et l’appel de méthode.  
  
    1.  Si le **aperçu des modifications - Réorganiser les paramètres** boîte de dialogue s’affiche, cliquez sur **appliquer**.  
  
         Dans cet exemple, la déclaration de méthode et tous les l’appel de méthode pour les sites `MethodB` sont mis à jour.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez réorganiser les paramètres à partir d’une déclaration de méthode ou un appel de méthode. Positionnez le curseur sur ou en regard de la déclaration de méthode ou du délégué, mais pas dans le corps.  
  
## <a name="see-also"></a>Voir aussi  
 [Refactorisation (C#)](../csharp-ide/refactoring-csharp.md)