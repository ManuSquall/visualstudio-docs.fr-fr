---
title: Ajouter l’attribut DebuggerDisplay
description: Découvrez comment ajouter l’attribut DebuggerDisplay pour contrôler la façon dont la fenêtre de variables du débogueur affiche un objet, une propriété ou un champ.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 2166f7876909f62d9d16a2a6d5ec126d4544193e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956722"
---
# <a name="add-debuggerdisplay-attribute"></a>Ajouter l’attribut DebuggerDisplay

Cette génération de code s’applique à :

- C#

**Ce qui suit :** L' [attribut DebuggerDisplay](../../debugger/using-the-debuggerdisplay-attribute.md) contrôle le mode d’affichage d’un objet, d’une propriété ou d’un champ dans les fenêtres de variables du débogueur.

Dans les **cas suivants :** Vous souhaitez [épingler](../../debugger/view-data-values-in-data-tips-in-the-code-editor.md#pin-properties-in-datatips) par programme des propriétés dans le débogueur dans votre code.

**Pourquoi :** L’épinglage de propriétés vous permet d’inspecter rapidement des objets en fonction de leurs propriétés en barbotant cette propriété en haut de la liste de propriétés de l’objet dans le débogueur. 

## <a name="how-to"></a>Procédures

1. Placez votre curseur sur un type, un délégué, une propriété ou un champ. 

2. Appuyez sur **CTRL** + **.** pour déclencher le menu **actions rapides et refactorisations** , puis sélectionnez **Ajouter un attribut DebuggerDisplay**.

    ![Générer des opérateurs de comparaison](media/add-debugger-display-attribute.png)

3. L’attribut DebuggerDisplay sera ajouté avec une méthode auto qui retourne la méthode ToString par défaut (). 

## <a name="see-also"></a>Voir aussi

- [Génération de code](../code-generation-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)