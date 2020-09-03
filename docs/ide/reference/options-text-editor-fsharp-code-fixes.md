---
title: Options, Éditeur de texte, F#, Correctifs du code
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c20646c8da4101ac674a64c5ca1ed23a3b1fd7b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770929"
---
# <a name="options-text-editor--f--code-fixes"></a>Options : éditeur de texte > les correctifs de code > F #

Utilisez la page d’options Correctifs du code pour spécifier les paramètres qui peuvent aider à identifier les erreurs de code et à proposer des solutions. Pour accéder à cette page d’options, choisissez **Outils**  >  **options**, puis **éditeur de texte**  >  **F #**  >  **correctifs de code**.

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

- [Général, environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)
- [Rechercher les modifications de code et d’autres historiques avec CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)
