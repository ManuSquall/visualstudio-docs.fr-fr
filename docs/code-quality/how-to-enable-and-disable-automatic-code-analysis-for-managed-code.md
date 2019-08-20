---
title: Activer ou désactiver l’analyse du code
ms.date: 10/25/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ec0a8a3f04830115d343fcef611cfbd338163395
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551032"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Procédure : Activer et désactiver l’analyse du code automatique pour le code managé

Vous pouvez configurer l’analyse du code (statique) pour qu’elle s’exécute après chaque génération d’un projet de code managé. Vous pouvez définir différentes propriétés d’analyse du code pour chaque configuration de build, par exemple, Debug et Release.

Cet article s’applique uniquement à l’analyse héritée et non à l’analyse du code en direct à l’aide d’analyseurs de [code](roslyn-analyzers-overview.md).

## <a name="to-enable-or-disable-automatic-code-analysis"></a>Pour activer ou désactiver l’analyse du code automatique

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis choisissez **Propriétés**.

1. Dans la boîte de dialogue Propriétés du projet, choisissez l’onglet **analyse du code** .

   > [!TIP]
   > Les nouveaux types de projets, tels que .NET Core et les applications .NET Standard, n’ont pas d’onglet **analyse du code** . L’analyse héritée n’est pas disponible pour ces types de projets, mais vous pouvez obtenir une analyse du code en temps réel à l’aide d' [analyseurs de code basés sur .NET Compiler Platform](roslyn-analyzers-overview.md). Pour supprimer les avertissements des analyseurs de code, consultez la remarque à la fin de cet article.

1. Spécifiez le type de build dans la **configuration** et la plateforme cible dans la **plateforme**.

1. Pour activer ou désactiver l’analyse du code automatique, activez ou désactivez la case à cocher **activer l’analyse du code sur la build** .

> [!NOTE]
> La case à cocher **activer l’analyse du code sur la build** affecte uniquement les analyses héritées. Elle n’affecte pas les analyseurs de [code basés sur .NET Compiler Platform](roslyn-analyzers-overview.md), qui s’exécutent toujours au moment de la génération si vous les avez installés en tant que package NuGet. Si vous souhaitez effacer les erreurs de l’analyseur de la **liste d’erreurs**, vous pouvez supprimer toutes les violations en cours en choisissant **analyser** > **exécuter l’analyse du code et supprimer les problèmes actifs** dans la barre de menus. Pour plus d’informations, consultez [Supprimer les violations](use-roslyn-analyzers.md#suppress-violations).
