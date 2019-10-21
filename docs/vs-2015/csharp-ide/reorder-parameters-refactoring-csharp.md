---
title: Réorganiser les paramètres de refactorisation (C#) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e39564fb108b63859620e2c4a650608cdf1e7e82
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673143"
---
# <a name="reorder-parameters-refactoring-c"></a>Réorganisation de la refactorisation de paramètres (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Reorder Parameters` est une opération C# de refactorisation visuelle qui fournit un moyen simple de modifier l’ordre des paramètres pour les méthodes, les indexeurs et les délégués. `Reorder Parameters` modifie la déclaration et, à tous les emplacements où le membre est appelé, les paramètres sont réorganisés pour refléter le nouvel ordre.

 Pour effectuer l’opération `Reorder Parameters`, placez le curseur sur ou à côté d’une méthode, d’un indexeur ou d’un délégué. Lorsque le curseur est en position, appelez l’opération `Reorder Parameters` en appuyant sur le raccourci clavier ou en cliquant sur la commande dans le menu contextuel.

> [!NOTE]
> Vous ne pouvez pas réorganiser le premier paramètre dans une méthode d’extension.

### <a name="to-reorder-parameters"></a>Pour réorganiser les paramètres

1. Créez une bibliothèque de classes nommée `ReorderParameters`, puis remplacez `Class1` par l’exemple de code suivant.

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

2. Placez le curseur sur `MethodB`, dans la déclaration de la méthode ou l’appel de la méthode.

3. Dans le menu **Refactoriser** , cliquez sur **Réorganiser les paramètres**.

     La boîte de dialogue **Réorganiser les paramètres** s’affiche.

4. Dans la boîte de dialogue **Réorganiser les paramètres** , sélectionnez `int i` dans la liste **paramètres** , puis cliquez sur le bouton enfoncé.

     Vous pouvez également faire glisser `int i` après `bool b` dans la liste des **paramètres** .

5. Dans la boîte de dialogue **Réorganiser les paramètres** , cliquez sur **OK**.

     Si l’option **aperçu des modifications** de la référence est sélectionnée dans la boîte de dialogue **Réorganiser les paramètres** , la boîte de dialogue **aperçu des modifications-réorganiser les paramètres** s’affiche. Il fournit un aperçu des modifications apportées à la liste de paramètres pour `MethodB` dans la signature et l’appel de la méthode.

    1. Si la boîte de dialogue **aperçu des modifications-réorganiser les paramètres** s’affiche, cliquez sur **appliquer**.

         Dans cet exemple, la déclaration de méthode et tous les sites d’appel de méthode pour `MethodB` sont mis à jour.

## <a name="remarks"></a>Notes
 Vous pouvez réorganiser les paramètres à partir d’une déclaration de méthode ou d’un appel de méthode. Placez le curseur sur ou en regard de la déclaration de méthode ou de délégué, mais pas dans le corps.

## <a name="see-also"></a>Voir aussi
 [Refactorisation (C#)](../csharp-ide/refactoring-csharp.md)