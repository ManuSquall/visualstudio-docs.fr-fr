---
title: Espaces de travail et les services de langage dans Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8631ffea-83c8-4fd4-a01e-c59772e89c84
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 551a621ab97c232970d6ef67da14379c5cdfbd46
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140805"
---
# <a name="workspaces-and-language-services"></a>Espaces de travail et les services de langage

Peuvent fournir des services de langage [ouvrir le dossier](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) les mêmes fonctionnalités de langage riche d’utilisateurs qu’ils sont utilisés pour lors de l’utilisation des solutions et projets. Un service de langage peut activer automatiquement en fonction de l’extension de fichier ou le contenu d’un document ouvert, bien que ce service de langage de « fichier libre » est limité à la mise en surbrillance de syntaxe. Informations supplémentaires sont requises pour fournir une expérience plus riche lors de la modification/révision du code source. Chaque service de langage a sa propre API pour l’initialisation avec ces données contextuelles supplémentaires pour un document. Cela est généralement gérée par un système de projet, qui est étroitement lié à la fois pour le service de langage et le système de génération.

## <a name="initialization"></a>Initialisation

Dans un [espace de travail](workspaces.md), les services de langage sont initialisés par une <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> point d’extension qui spécialise uniquement dans ce service de langage et ne sait rien de la création de la build. De cette façon, le propriétaire d’un service de langage peut gérer un seul dossier ouvert extension quel que soit le nombre de modèles existent dans des dossiers et des fichiers pour l’exécution de leur du compilateur pendant une génération (par exemple MSBuild, makefiles, etc.). Lorsque les fichiers à partir de laquelle un contexte de fichier a été créé sont modifiées sur le disque et le contexte du fichier est actualisé, le fournisseur de service de langage est informé de l’ensemble de mises à jour des contextes de fichier. Le fournisseur de service de langage peut puis mettre à jour son modèle.

Lorsqu’un document est ouvert dans l’éditeur, Visual Studio considère uniquement la langue des fournisseurs de services qui requièrent des types de contexte de fichier pour lequel un fournisseur de contexte de fichier correspondants sont accessibles. Il passe ensuite le contexte de fichier (s) à partir du fournisseur (s) correspondant au fournisseur de services de langue sélectionnée via `ILangaugeServiceProvider.InitializeAsync`. Ce que le fournisseur de service de langage fait avec que les données de contexte de fichier sont un détail d’implémentation du fournisseur de services de langage, mais l’expérience utilisateur attendu est un service de langage plus riche pour que d’ouvrir le document.

## <a name="using-ilanguageserviceprovider"></a>À l’aide de ILanguageServiceProvider

Le service de langage soient prévenu lorsqu’un contexte de fichier est créé avec un `ContextType` qui correspond à l’un de le `SupportedContextTypes` valeurs du serveur langue export (attribut).

Pour prendre en charge un service de langage, une extension devez :

- Unique `Guid`. Il sera utilisé pour `SupportedContextTypes` arguments d’attribut et dans un `FileContext` objet.
- Contexte du langage
  - Fabrique de fournisseurs
    - `ExportFileContextProviderAttribute` attribut avec ci-dessus identifie de façon unique généré `Guid` dans `SupportedContextTypes`
    - Implémente `IWorkspaceProviderFactory<IFileContextProvider>`
  - Implémentation du fournisseur de `IFileContextProvider.GetContextsForFileAsync`
    - Construire une nouvelle `FileContext` avec la `contextType` argument du constructeur en tant que le généré de manière unique `Guid`
    - Utilisez le `Context` propriété de la `FileContext` pour fournir des données supplémentaires à la `ILanguageServiceProvider`
- Service de langage
  - Fabrique de fournisseurs
    - `ExportLanguageServiceProvider` attribut avec ci-dessus identifie de façon unique généré `Guid` dans `SupportedContextTypes`
    - Implémente `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - Fournisseur
    - Implémente `ILanguageServiceProvider`
    - Utilisez `ILanguageServiceProvider.InitializeAsync` pour activer les services de langage pour les arguments fournis lorsqu’un fichier est ouvert.
    - Utilisez `ILanguageServiceProvider.UninitializeAsync` pour désactiver les services de langage pour les arguments fournis quand un fichier est fermé

>[!WARNING]
>Le `ILanguageServiceProvider` méthodes peuvent être appelées par l’espace de travail sur le thread principal. Pensez à planifier le travail sur un thread différent pour éviter d’introduire des retards d’interface utilisateur.

## <a name="language-server-protocol"></a>Protocole de serveur de langage

Le `Microsoft.VisualStudio.Workspace.*` API ne sont pas la seule façon d’activer votre service de langage dans le dossier ouvert. Une autre option consiste à utiliser un serveur de langue. Pour plus d’informations, consultez la [protocole de serveur de langage](language-server-protocol.md).

## <a name="related-interfaces"></a>Interfaces associées

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> est appelé lorsqu’un fichier de mise en correspondance des types de fichier est ouvert ou fermé pour la modification.

## <a name="next-steps"></a>Étapes suivantes

* [Génération de l’espace de travail](workspace-build.md) -prend en charge d’ouvrir le dossier créer des systèmes tels que MSBuild et les makefiles. 