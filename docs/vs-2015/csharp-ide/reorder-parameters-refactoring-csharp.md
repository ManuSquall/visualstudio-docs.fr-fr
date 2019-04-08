---
title: Réorganiser les paramètres (refactorisation C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 9bec38846f7703ff3958aa1c0fcc9a660a5e080d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951371"
---
# <a name="reorder-parameters-refactoring-c"></a>Réorganisation de la refactorisation de paramètres (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Reorder Parameters` est un Visual C# opération de refactorisation qui offre un moyen facile pour modifier l’ordre des paramètres pour les méthodes, indexeurs et délégués. `Reorder Parameters` Modifie la déclaration, et à tous les emplacements où le membre est appelé, les paramètres sont réorganisés pour refléter le nouvel ordre.  
  
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