---
title: Espaces de travail et les services de langage dans Visual Studio | Microsoft Docs
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
ms.openlocfilehash: be9fb8c1e3ae363898e0438bdd1ec34c9fd23727
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735462"
---
# <a name="workspaces-and-language-services"></a>Espaces de travail et les services de langage

Services de langage peuvent fournir [ouvrir le dossier](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) utilisateurs les mêmes fonctionnalités de langage riche qu’ils sont utilisés pour lorsque vous travaillez avec les solutions et projets. Un service de langage peut activation automatique en fonction de l’extension de fichier ou le contenu d’un document ouvert, bien que ce service de langage « fichier libre » est limité à la coloration syntaxique. Informations supplémentaires sont requises pour fournir une expérience plus riche lors de la modification/révision du code source. Chaque service de langage possède sa propre API pour l’initialisation avec ces données contextuelles supplémentaires pour un document. Elle est généralement gérée par un système de projet, qui est étroitement lié à la fois pour le service de langage et le système de génération.

## <a name="initialization"></a>Initialisation

Dans un [espace de travail](workspaces.md), services de langage sont initialisés par une <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> point d’extension qui spécialise uniquement dans ce service de langage et ne sait rien de la création de la build. De cette façon, le propriétaire d’un service de langage peut gérer un seul dossier ouvert extension indépendamment de la façon dont de nombreux modèles existent dans les dossiers et fichiers pour l’exécution de leur du compilateur pendant une génération (par exemple MSBuild, makefiles, etc.). Lorsque les fichiers à partir duquel un contexte de fichier a été créé sont modifiés sur le disque et le contexte du fichier est actualisé, le fournisseur de service de langage est averti de l’ensemble de mises à jour des contextes de fichier. Le fournisseur de service de langage peut puis mettez à jour son modèle.

Lorsqu’un document est ouvert dans l’éditeur, Visual Studio considère uniquement la langue des fournisseurs de services qui requièrent des types de contexte de fichier pour lequel un fournisseur de contexte de fichier correspondant sont accessibles. Il passe ensuite le contexte de fichier (s) à partir des ou les fournisseurs correspondants au fournisseur de services de langue sélectionnée via `ILanguageServiceProvider.InitializeAsync`. Ce que le fournisseur de service de langage fait que les données de contexte de fichier sont un détail d’implémentation du fournisseur de services de langage, mais l’expérience utilisateur attendu est un service de langage plus riche pour que d’ouvrir le document.

## <a name="using-ilanguageserviceprovider"></a>À l’aide de ILanguageServiceProvider

Le service de langage sera averti lorsqu’un contexte de fichier est créé avec un `ContextType` qui correspond à l’un de le `SupportedContextTypes` valeurs du serveur de langage export (attribut).

Pour prendre en charge un service de langage, une extension devez :

- Une valeur unique `Guid`. Il sera utilisé pour `SupportedContextTypes` arguments d’attribut et dans un `FileContext` objet.
- Contexte de fichier de langage
  - Fabrique de fournisseur
    - `ExportFileContextProviderAttribute` attribut avec la méthode ci-dessus identifie de façon unique généré `Guid` dans `SupportedContextTypes`
    - Implémente `IWorkspaceProviderFactory<IFileContextProvider>`
  - Implémentation de fournisseur de `IFileContextProvider.GetContextsForFileAsync`
    - Construire une nouvelle `FileContext` avec la `contextType` argument du constructeur en tant que de manière unique généré `Guid`
    - Utilisez le `Context` propriété de la `FileContext` pour fournir des données supplémentaires à la `ILanguageServiceProvider`
- service de langage
  - Fabrique de fournisseur
    - `ExportLanguageServiceProvider` attribut avec la méthode ci-dessus identifie de façon unique généré `Guid` dans `SupportedContextTypes`
    - Implémente `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - Fournisseur
    - Implémente `ILanguageServiceProvider`
    - Utilisez `ILanguageServiceProvider.InitializeAsync` pour activer les services de langage pour les arguments fournis quand un fichier est ouvert.
    - Utilisez `ILanguageServiceProvider.UninitializeAsync` pour désactiver les services de langage pour les arguments fournis quand un fichier est fermé

>[!WARNING]
>Le `ILanguageServiceProvider` méthodes peuvent être appelées par l’espace de travail sur le thread principal. Pensez à planifier le travail sur un thread différent afin d’éviter d’introduire des retards de l’interface utilisateur.

## <a name="language-server-protocol"></a>Protocole de serveur de langage

Le `Microsoft.VisualStudio.Workspace.*` API ne sont pas la seule façon d’activer votre service de langage dans le dossier ouvert. Une autre option consiste à utiliser un serveur de langue. Pour plus d’informations, consultez le [protocole de serveur de langage](language-server-protocol.md).

## <a name="related-interfaces"></a>Interfaces connexes

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> est appelé lorsqu’un fichier de mise en correspondance des types de fichier est ouvert ou fermé pour la modification.

## <a name="next-steps"></a>Étapes suivantes

* [Génération de l’espace de travail](workspace-build.md) -prend en charge d’ouvrir le dossier créer des systèmes tels que MSBuild et makefiles. 