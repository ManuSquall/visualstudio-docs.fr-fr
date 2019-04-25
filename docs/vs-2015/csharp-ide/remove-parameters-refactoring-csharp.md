---
title: Supprimer les paramètres (refactorisation c#) | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a28076b8c394818c248a5a18c7bc91d484f2c28a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045796"
---
# <a name="remove-parameters-refactoring-c"></a>Supprimer les paramètres (Refactorisation C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Remove Parameters` est une opération de refactorisation qui offre un moyen facile de supprimer des paramètres des méthodes, des indexeurs ou des délégués. Supprimer les paramètres modifie la déclaration ; pour tous les emplacements où le membre est appelé, le paramètre est supprimé afin de refléter la nouvelle déclaration.  
  
 Vous effectuez l’opération Supprimer les paramètres en positionnant le curseur sur une méthode, un indexeur ou un délégué d’abord. Lorsque le curseur est en position, pour appeler la supprimer `Parameters` opération, cliquez sur le **refactoriser** menu, appuyez sur le raccourci clavier, ou sélectionnez la commande dans le menu contextuel.  
  
> [!NOTE]
>  Vous ne pouvez pas supprimer le premier paramètre dans une méthode d’extension.  
  
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
  
2. Placez le curseur sur la méthode `A`, soit dans la déclaration de méthode ou de l’appel de méthode.  
  
3. À partir de la **refactoriser** menu, sélectionnez **supprimer les paramètres** pour afficher le **supprimer les paramètres** boîte de dialogue.  
  
     Vous pouvez également taper le raccourci clavier CTRL + R, V pour afficher le **supprimer les paramètres** boîte de dialogue.  
  
     Vous pouvez également cliquer sur le curseur, pointer vers **refactoriser**, puis cliquez sur **supprimer les paramètres** pour afficher le **supprimer les paramètres** boîte de dialogue.  
  
4. À l’aide de la **paramètres** champ, positionnez le curseur sur `int i`, puis cliquez sur **supprimer**.  
  
5. Cliquez sur **OK**.  
  
6. Dans le **aperçu des modifications, supprimer les paramètres** boîte de dialogue, cliquez sur **appliquer**.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez supprimer les paramètres à partir d’une déclaration de méthode ou un appel de méthode. Positionnez le curseur dans le nom de déclaration ou de délégué de méthode et supprimer des paramètres d’appel.  
  
> [!CAUTION]
>  Supprimez Active des paramètres vous permet de supprimer un paramètre qui est référencé dans le corps du membre, mais il ne supprimez pas les références à ce paramètre dans le corps de méthode. Cela peut introduire des erreurs de build dans votre code. Toutefois, vous pouvez utiliser la **aperçu des modifications** boîte de dialogue pour passer en revue votre code avant d’exécuter l’opération de refactorisation.  
  
 Si un paramètre en cours de suppression est modifié pendant l’appel à une méthode, la suppression du paramètre supprimera également la modification. Par exemple, si un appel de méthode est modifié à partir de  
  
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