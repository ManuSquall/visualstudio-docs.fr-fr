---
title: Désactiver l’analyse du code hérité
ms.date: 10/04/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c00a66a856dccb0ccb488937b935d9150ffc0266
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975081"
---
# <a name="how-to-enable-and-disable-binary-code-analysis-for-managed-code"></a>Procédure : Activer et désactiver l’analyse du code binaire pour le code managé

Vous pouvez configurer l’analyse du code hérité (analyse binaire) pour qu’elle s’exécute après chaque génération d’un projet de code managé. Vous pouvez également avoir des paramètres différents pour chaque configuration de build, par exemple, Debug et Release.

> [!NOTE]
> L’analyse héritée n’est pas disponible pour les nouveaux types de projets, tels que .NET Core et les applications .NET Standard. Ces projets utilisent des [analyseurs de code basés sur .NET Compiler Platform](roslyn-analyzers-overview.md) pour analyser le code, en direct et au moment de la génération. Pour plus d’informations sur la désactivation de l’analyse du code source dans ces projets, consultez [Comment désactiver l’analyse du code source](disable-code-analysis.md).

Pour activer ou désactiver l’analyse du code hérité :

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis choisissez **Propriétés**.

2. Dans la boîte de dialogue Propriétés du projet, choisissez l’onglet **analyse du code** .

3. Spécifiez le type de build dans la **configuration** et la plateforme cible dans la **plateforme**. (Projets standard Non-.NET Core/. NET uniquement.)

::: moniker range="vs-2017"

4. Pour activer ou désactiver l’analyse du code automatique, activez ou désactivez la case à cocher **activer l’analyse du code sur la build** .

::: moniker-end

::: moniker range=">=vs-2019"

4. Pour activer ou désactiver l’analyse du code automatique, activez ou désactivez la case à cocher **exécuter lors** de la génération dans la section **analyseurs binaires** .

   ![Exécuter l’analyse du code binaire sur l’option de génération dans Visual Studio](media/run-on-build-binary-analyzers.png)

::: moniker-end

> [!NOTE]
> La désactivation de l’analyse du code binaire sur la build n’affecte pas les [analyseurs de code basés sur .NET Compiler Platform](roslyn-analyzers-overview.md), qui s’exécutent toujours au moment de la génération si vous les avez installés en tant que package NuGet. Pour plus d’informations sur la désactivation de l’analyse à partir de ces analyseurs, consultez [Comment désactiver l’analyse du code source](disable-code-analysis.md).