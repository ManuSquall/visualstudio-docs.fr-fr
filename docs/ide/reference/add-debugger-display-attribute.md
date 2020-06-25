---
title: Ajouter l’attribut DebuggerDisplay
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 611df048d4ce569c10ae933be9053acf1174c06f
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290353"
---
# <a name="add-debuggerdisplay-attribute"></a>Ajouter l’attribut DebuggerDisplay

Cette génération de code s’applique à :

- C#

**Ce qui suit :** L' [attribut DebuggerDisplay](https://docs.microsoft.com/visualstudio/debugger/using-the-debuggerdisplay-attribute) contrôle le mode d’affichage d’un objet, d’une propriété ou d’un champ dans les fenêtres de variables du débogueur.

Dans les **cas suivants :** Vous souhaitez [épingler](https://docs.microsoft.com/visualstudio/debugger/view-data-values-in-data-tips-in-the-code-editor#pin-properties-in-datatips) par programme des propriétés dans le débogueur dans votre code.

**Pourquoi :** L’épinglage de propriétés vous permet d’inspecter rapidement des objets en fonction de leurs propriétés en barbotant cette propriété en haut de la liste de propriétés de l’objet dans le débogueur. 

## <a name="how-to"></a>Procédures

1. Placez votre curseur sur un type, un délégué, une propriété ou un champ. 

2. Appuyez sur **CTRL** + **.** pour déclencher le menu **actions rapides et refactorisations** , puis sélectionnez **Ajouter un attribut DebuggerDisplay**.

    ![Générer des opérateurs de comparaison](media/add-debugger-display-attribute.png)

3. L’attribut DebuggerDisplay sera ajouté avec une méthode auto qui retourne la méthode ToString par défaut (). 

## <a name="see-also"></a>Voir aussi

- [Génération de code](../code-generation-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
