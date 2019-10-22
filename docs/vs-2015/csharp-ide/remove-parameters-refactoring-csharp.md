---
title: Supprimer les paramètres (),C#refactorisation () | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.remove
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], removing
- refactoring [C#], Remove Parameters
- Remove Parameters refactoring [C#]
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40c373c3575f007952143e29c8dfc2cfac3d080f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667490"
---
# <a name="remove-parameters-refactoring-c"></a>Supprimer les paramètres (Refactorisation C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Remove Parameters` est une opération de refactorisation qui fournit un moyen simple de supprimer des paramètres de méthodes, d’indexeurs ou de délégués. Supprimer les paramètres modifie la déclaration. à tous les emplacements où le membre est appelé, le paramètre est supprimé pour refléter la nouvelle déclaration.

 Pour effectuer l’opération Remove Parameters, commencez par positionner le curseur sur une méthode, un indexeur ou un délégué. Lorsque le curseur est en position, pour appeler l’opération de suppression de `Parameters`, cliquez sur le menu **Refactoriser** , appuyez sur le raccourci clavier ou sélectionnez la commande dans le menu contextuel.

> [!NOTE]
> Vous ne pouvez pas supprimer le premier paramètre dans une méthode d’extension.

### <a name="to-remove-parameters"></a>Pour supprimer des paramètres

1. Créez une application console nommée `RemoveParameters`, puis remplacez `Program` par le code suivant.

    ```csharp
    class A
    {
        // Invoke on 'A'.
        public A(string s, int i) { }
    }

    class B
    {
        void C()
        {
            // Invoke on 'A'.
            A a = new A("a", 2);
        }
    }
    ```

2. Placez le curseur sur la `A` de la méthode, dans la déclaration de la méthode ou l’appel de la méthode.

3. Dans le menu **Refactoriser** , sélectionnez **Supprimer les paramètres** pour afficher la boîte de dialogue **Supprimer les paramètres** .

     Vous pouvez également taper le raccourci clavier CTRL + R, V pour afficher la boîte de dialogue **Supprimer les paramètres** .

     Vous pouvez également cliquer avec le bouton droit sur le curseur, pointer sur **Refactoriser**, puis cliquer sur **Supprimer les paramètres** pour afficher la boîte de dialogue **Supprimer les paramètres** .

4. À l’aide du champ **paramètres** , positionnez le curseur sur `int i`, puis cliquez sur **supprimer**.

5. Cliquez sur **OK**.

6. Dans la boîte de dialogue **aperçu des modifications — supprimer les paramètres** , cliquez sur **appliquer**.

## <a name="remarks"></a>Notes
 Vous pouvez supprimer des paramètres d’une déclaration de méthode ou d’un appel de méthode. Placez le curseur dans la déclaration de méthode ou le nom du délégué et appelez Remove Parameters.

> [!CAUTION]
> Supprimer les paramètres vous permet de supprimer un paramètre qui est référencé dans le corps du membre, mais il ne supprime pas les références à ce paramètre dans le corps de la méthode. Cela peut introduire des erreurs de build dans votre code. Toutefois, vous pouvez utiliser la boîte de dialogue **aperçu des modifications** pour vérifier votre code avant d’exécuter l’opération de refactorisation.

 Si un paramètre en cours de suppression est modifié pendant l’appel à une méthode, la suppression du paramètre supprimera également la modification. Par exemple, si un appel de méthode est modifié de

```csharp
MyMethod(param1++, param2);
```

 par celle-ci :

```csharp
MyMethod(param2);
```

 par l’opération de refactorisation, `param1` n’est pas incrémenté.

## <a name="see-also"></a>Voir aussi
 [Refactorisation (C#)](../csharp-ide/refactoring-csharp.md)