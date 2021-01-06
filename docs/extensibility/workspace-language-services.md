---
title: Espaces de travail et services de langage dans Visual Studio | Microsoft Docs
description: Découvrez comment les services de langage peuvent fournir aux utilisateurs de dossiers ouverts les mêmes fonctionnalités de langage enrichies qu’ils utilisent lors de l’utilisation de solutions et de projets.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 815cfb9e17fed38b519719010acd997f7fdc5242
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877037"
---
# <a name="workspaces-and-language-services"></a>Espaces de travail et services de langage

Les services de langage peuvent fournir aux utilisateurs du [dossier ouvert](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) les mêmes fonctionnalités de langage enrichies que celles auxquelles ils sont utilisés lors de l’utilisation de solutions et de projets. Un service de langage peut s’activer automatiquement en fonction de l’extension de fichier ou du contenu d’un document ouvert, bien que ce service de langage de « fichier libre » soit limité à la mise en surbrillance de la syntaxe. Des informations supplémentaires sont requises pour fournir une expérience plus riche lors de la modification et de la révision du code source. Chaque service de langage possède sa propre API pour l’initialisation avec ces données contextuelles supplémentaires pour un document. Cela est généralement géré par un système de projet, qui est étroitement couplé à la fois au service de langage et au système de génération.

## <a name="initialization"></a>Initialisation

Dans un [espace de travail](workspaces.md), les services de langage sont initialisés par un <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> point d’extension qui est spécialisé uniquement dans ce service de langage et ne sait rien de la création de builds. De cette façon, un propriétaire du service de langage peut conserver une extension de dossier ouverte unique, indépendamment du nombre de modèles dans les dossiers et les fichiers pour l’exécution de leur compilateur pendant une génération (par exemple MSBuild, makefiles, etc.). Lorsque des fichiers à partir desquels un contexte de fichier a été créé sont modifiés sur le disque et que le contexte de fichier est actualisé, le fournisseur de services de langage est informé de l’ensemble mis à jour des contextes de fichier. Le fournisseur de services de langage peut ensuite mettre à jour son modèle.

Quand un document est ouvert dans l’éditeur, Visual Studio considère uniquement les fournisseurs de services de langage qui requièrent des types de contexte de fichier pour lesquels un fournisseur de contexte de fichier correspondant est disponible. Il passe ensuite le ou les contextes de fichier du ou des fournisseurs correspondants au fournisseur de services de langage sélectionné via `ILanguageServiceProvider.InitializeAsync` . Ce que fait le fournisseur du service de langage avec ce fichier les données de contexte est un détail d’implémentation du fournisseur de services de langage, mais l’expérience utilisateur attendue est un service de langage plus élaboré pour ce document ouvert.

## <a name="using-ilanguageserviceprovider"></a>Utilisation de ILanguageServiceProvider

Le service de langage est averti lorsqu’un contexte de fichier est créé avec un `ContextType` qui correspond à l’une des `SupportedContextTypes` valeurs de l’attribut d’exportation du serveur de langage.

Pour prendre en charge un service de langage, une extension aura besoin des éléments suivants :

- Unique `Guid` . Ce sera utilisé pour les `SupportedContextTypes` arguments d’attribut et dans un `FileContext` objet.
- Contexte du fichier de langage
  - Fabrique de fournisseurs
    - `ExportFileContextProviderAttribute` attribut avec les éléments ci-dessus générés de manière unique `Guid` dans `SupportedContextTypes`
    - Implémente `IWorkspaceProviderFactory<IFileContextProvider>`
  - Implémentation du fournisseur de `IFileContextProvider.GetContextsForFileAsync`
    - Construit un nouveau `FileContext` avec l' `contextType` argument de constructeur comme étant généré de manière unique `Guid`
    - Utilisez la `Context` propriété du `FileContext` pour attribuer des données supplémentaires au `ILanguageServiceProvider`
- Service de langage
  - Fabrique de fournisseurs
    - `ExportLanguageServiceProvider` attribut avec les éléments ci-dessus générés de manière unique `Guid` dans `SupportedContextTypes`
    - Implémente `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - Fournisseur
    - Implémente `ILanguageServiceProvider`
    - Utilisez `ILanguageServiceProvider.InitializeAsync` pour activer les services de langage pour les arguments fournis lors de l’ouverture d’un fichier
    - Utilisez `ILanguageServiceProvider.UninitializeAsync` pour désactiver les services de langage pour les arguments fournis lorsqu’un fichier est fermé.

>[!WARNING]
>Les `ILanguageServiceProvider` méthodes peuvent être appelées par l’espace de travail sur le thread principal. Envisagez de planifier le travail sur un thread différent afin d’éviter d’introduire des retards d’interface utilisateur.

## <a name="language-server-protocol"></a>Protocole de serveur de langage

Les `Microsoft.VisualStudio.Workspace.*` API ne sont pas le seul moyen d’activer votre service de langage dans un dossier ouvert. Une autre option consiste à utiliser un serveur de langage. Pour plus d’informations, consultez la en savoir plus sur le [protocole du serveur de langage](language-server-protocol.md).

## <a name="related-interfaces"></a>Interfaces associées

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> est appelée lorsqu’un fichier de types de fichiers correspondants est ouvert ou fermé pour modification.

## <a name="next-steps"></a>Étapes suivantes

* [Espace de travail génération](workspace-build.md) : le dossier ouvert prend en charge les systèmes de génération tels que MSBuild et makefiles.