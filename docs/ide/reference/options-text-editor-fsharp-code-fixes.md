---
title: Options, Éditeur de texte, F#, Correctifs du code
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a5c736be59c257d98085831971d6b7b9dc2a0ef3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72666281"
---
# <a name="options-text-editor--f--code-fixes"></a>Options : L’éditeur de texte > les correctifs de code > de F

Utilisez la page d’options Correctifs du code pour spécifier les paramètres qui peuvent aider à identifier les erreurs de code et à proposer des solutions. Pour accéder à cette page d’options, choisissez **Tools** > **Options,** puis choisissez **Text Editor** > **F '** > **Code Fixes**.

## <a name="code-fixes"></a>Correctifs du code

- **Simplifier les noms (supprimer les qualificateurs inutiles)**

  Si cette case est cochée, les noms qualifiés complets sont simplifiés quand les qualifications ne sont pas nécessaires, comme pour un membre d’un espace de noms fréquemment utilisé.

- **Placer toujours les instructions open au niveau supérieur**

  Si cette case est cochée et que vous tapez une instruction `open` dans le code, elle est placée au niveau supérieur.

- **Supprimer les instructions open inutilisées**

  Si cette case à cocher est activée, les documents sont analysés pour rechercher les instructions `open` inutilisées et une ampoule [Action rapide](../quick-actions.md) s’affiche avec une action pour supprimer toutes les instructions `open` inutilisées.

- **Analyser et suggérer des correctifs pour les valeurs inutilisées**

  Si cette case est cochée, l’outil reconnaît une valeur qui n’est pas utilisée dans le code. Ensuite, si vous pointez sur la valeur inutilisée, il vous recommande des moyens d’utiliser la valeur.

## <a name="see-also"></a>Voir aussi

- [Général, Environnement, Options Dialog Box](../../ide/reference/general-environment-options-dialog-box.md)
- [Rechercher les modifications de code et d’autres historiques avec CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)
