---
title: Options, Éditeur de texte, F#, Correctifs du code
ms.date: 01/16/2019
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.FSharp.Code_Fixes
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: bbe6b49d7b80138c7fc465e1c86aa13e6bc5e92d
ms.sourcegitcommit: 8bfabab73b39b3b3e68a3e8dc225515e8b310fed
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2019
ms.locfileid: "54398388"
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