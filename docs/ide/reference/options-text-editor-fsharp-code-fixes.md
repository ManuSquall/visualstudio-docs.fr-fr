---
title: Options, Éditeur de texte, F#, Correctifs du code
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bb9daee86fec058fca68740eaea3b9436e5570d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778539"
---
# <a name="options-text-editor-f-code-fixes"></a>Options, Éditeur de texte, F#, Correctifs du code

Utilisez la page d’options **Correctifs du code** pour spécifier les paramètres qui peuvent aider à identifier les erreurs de code et à proposer des solutions. Pour accéder à cette page d’options, choisissez **Outils** > **Options**, puis **Éditeur de texte** > **F#** > **Correctifs du code**.

## <a name="code-fixes"></a>Correctifs du code

- **Simplifier les noms (supprimer les qualificateurs inutiles)**

   Si cette case est cochée, les noms qualifiés complets sont simplifiés quand les qualifications ne sont pas nécessaires, comme pour un membre d’un espace de noms fréquemment utilisé.

- **Placer toujours les instructions open au niveau supérieur**

   Si cette case est cochée et que vous tapez une instruction open dans le code, elle est placée au niveau supérieur.

- **Supprimer les instructions open inutilisées**

   Si cette case est cochée, les instructions open dans le fichier actuel qui ne sont pas utilisées sont supprimées.

- **Analyser et suggérer des correctifs pour les valeurs inutilisées**

   Si cette case est cochée, l’outil reconnaît une valeur qui n’est pas utilisée dans le code. Ensuite, si vous pointez sur la valeur inutilisée, il vous recommande des moyens d’utiliser la valeur.

## <a name="see-also"></a>Voir aussi

- [Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)
- [Rechercher les modifications de code et d’autres historiques avec CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)