---
title: Activer ou désactiver l’analyse du code
ms.date: 10/25/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 4878c25021d87e91f6a575d11a876d7aac2455d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816241"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Procédure : Activer et désactiver l’analyse du code automatique pour le code managé

Vous pouvez configurer l’analyse du code (statique) à exécuter après chaque génération d’un projet de code managé. Vous pouvez définir des propriétés d’analyse pour chaque configuration de build de code différents, par exemple, debug et release.

Cet article s’applique à l’analyse du code uniquement comme étant statique et l’analyse du code pas en temps réel à l’aide [analyseurs de code Roslyn](roslyn-analyzers-overview.md).

## <a name="to-enable-or-disable-automatic-code-analysis"></a>Pour activer ou désactiver l’analyse du code automatique

1. Dans **l’Explorateur de solutions**, cliquez sur le projet, puis choisissez **propriétés**.

1. Dans la boîte de dialogue Propriétés du projet, choisissez le **analyse du Code** onglet.

   > [!TIP]
   > Les types de projet plus récent tels que des applications .NET Core et .NET Standard n’ont pas un **analyse du Code** onglet. Analyse statique du code n’est pas disponible pour ces types de projets, mais vous pouvez toujours obtenir d’analyse du code en temps réel à l’aide [analyseurs de code Roslyn](roslyn-analyzers-overview.md). Pour supprimer les avertissements d’analyseurs de Roslyn de code, consultez la Remarque à la fin de cet article.

1. Spécifiez le type de build dans **Configuration** et la plateforme cible dans **plateforme**.

1. Pour activer ou désactiver l’analyse du code automatique, activez ou désactivez le **activer l’analyse du Code sur la Build** case à cocher.

> [!NOTE]
> Le **activer l’analyse du Code sur la Build** case à cocher affecte uniquement l’analyse statique du code. Cela n’affecte pas [analyseurs de code Roslyn](roslyn-analyzers-overview.md), qui s’exécutent toujours à la conférence build si vous avez installé les comme package NuGet. Si vous souhaitez effacer les erreurs de l’Analyseur de la **liste d’erreurs**, vous pouvez supprimer toutes les violations actuelles en choisissant **analyser** > **exécuter l’analyse du Code et supprimer Active Problèmes** sur la barre de menus. Pour plus d’informations, consultez [supprimer violations](use-roslyn-analyzers.md#suppress-violations).
