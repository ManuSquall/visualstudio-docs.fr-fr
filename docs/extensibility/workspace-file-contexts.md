---
title: Contextes de fichier d’espace de travail dans Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 36f986db6f2c7b483b46060e1f514acc8dd9e758
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952811"
---
# <a name="workspace-file-contexts"></a>Contextes de fichier d’espace de travail

Toutes les informations sur [ouvrir le dossier](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) espaces de travail sont produites par « fichier contexte fournisseurs » qui implémentent le <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> interface. Ces extensions peuvent rechercher des modèles dans des dossiers ou fichiers, lire les fichiers de MSBuild et makefiles, détectent les dépendances de package, etc. afin de s’accumuler les insights que dont ils ont besoin définir un contexte de fichier. Un contexte de fichier en lui-même n’effectue aucune action, mais fournit plutôt les données sur lesquelles peut agir puis une autre extension.

Chaque <xref:Microsoft.VisualStudio.Workspace.FileContext> a un `Guid` associé qui identifie le type de données qu’il exécute. Un espace de travail utilise cette `Guid` ultérieurement à concordent avec les extensions qui consomment les données via le <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> propriété. Un fournisseur de contexte du fichier exporté avec les métadonnées qui identifie le contexte de fichier `Guid`s qu’elle peut produire des données pour.

Une fois défini, un contexte de fichier peut être associé à n’importe quel nombre de fichiers ou dossiers dans l’espace de travail. Un fichier donné ou un dossier peut être associé à n’importe quel nombre de contextes de fichier. Il est une relation plusieurs-à-plusieurs.

Les scénarios les plus courants pour les contextes de fichier sont liées à la build, de débogage et de services de langage. Pour plus d’informations, consultez les autres rubriques relatives à ces scénarios.

## <a name="file-context-lifecycle"></a>Cycle de vie du contexte de fichier

Cycles de vie pour un `FileContext` sont non déterministes. À tout moment, un composant peut demander de manière asynchrone pour un jeu de types de contexte. Les fournisseurs qui prennent en charge un sous-ensemble des types de contexte de requête doivent être interrogées. Le `IWorkspace` instance joue le rôle d’intermédiaire entre les consommateurs et les fournisseurs via le <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> (méthode). Les consommateurs peuvent demander un contexte et effectuer une action à court terme basée sur le contexte, alors que d’autres peuvent demander un contexte et conserver une référence à long terme.

Modifications peuvent se produire dans des fichiers qui provoquent un contexte de fichier devenir obsolète. Le fournisseur peut déclencher un événement sur le `FileContext` pour avertir les consommateurs des mises à jour. Par exemple, si un contexte de build est fourni pour un fichier, mais une modification sur disque invalide ce contexte, le producteur d’origine peut appeler l’événement. Les consommateurs qui référence encore `FileContext` pouvez puis actualiser pour un nouveau `FileContext`.

>[!NOTE]
>Il n’existe aucun modèle push à des consommateurs. Les consommateurs ne sont pas avertis d’un fournisseur de nouveau `FileContext` après leur demande.

## <a name="expensive-file-context-computations"></a>Calculs de contexte de fichiers coûteux

Contenu du fichier lecture à partir du disque peut être coûteuse, en particulier lorsqu’un fournisseur doit résoudre la relation entre les fichiers. Par exemple, un fournisseur peut-être être interrogé pour le contexte du fichier d’un fichier source, mais le contexte du fichier dépend de métadonnées à partir d’un fichier de projet. L’analyse du fichier de projet ou de l’évaluation avec MSBuild est coûteuse. Au lieu de cela, l’extension peut exporter un `IFileScanner` créer `FileDataValue` les données lors de l’espace de travail d’indexation. Maintenant lorsque vous êtes invité pour les contextes de fichier, le `IFileContextProvider` peuvent interroger rapidement pour que les données indexées. Pour plus d’informations sur l’indexation, consultez le [espace de travail d’indexation](workspace-indexing.md) rubrique.

>[!WARNING]
>Méfiez-vous des autres méthodes votre `FileContext` peuvent être coûteuses à calculer. Certaines interactions de l’interface utilisateur sont synchrones et s’appuient sur un volume élevé de `FileContext` demandes. Ouverture d’un onglet de l’éditeur et l’ouverture des exemples un **l’Explorateur de solutions** menu contextuel. Ces actions rendre nombreux build contexte tapez des requêtes.

## <a name="file-context-related-apis"></a>API associées au contexte de fichier

- <xref:Microsoft.VisualStudio.Workspace.FileContext> contient les données et métadonnées.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> et <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> créer le contexte du fichier.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> Exporte un fournisseur de contexte de fichier.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> est utilisé pour les consommateurs pour obtenir des contextes de fichier.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> définit les types de contexte de build qui consommera d’ouvrir le dossier.

## <a name="file-context-actions"></a>Actions de contexte de fichier

Pendant un `FileContext` lui-même est uniquement les données sur un ou plusieurs fichiers, un <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> est un moyen d’exprimer et d’agir sur ces données. `IFileContextAction` est flexible dans son utilisation. Deux de ses scénarios les plus courants sont de génération et de débogage.

## <a name="reporting-progress"></a>Signaler la progression

Le <xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A> est transmis à la méthode `IProgress<IFileContextActionProgressUpdate>`, mais l’argument ne doit pas être utilisé en tant que type. `IFileContextActionProgressUpdate` est une interface vide et l’appel de `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` peut lever `NotImplementedException`. Au lieu de cela, le `IFileContextAction` doit convertir l’argument en un autre type en fonction des besoins pour le scénario.

Pour plus d’informations sur les types dans Visual Studio, consultez documentation du scénario respectif.

## <a name="file-context-action-related-apis"></a>API associées à une action de contexte de fichier

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> exécute un comportement selon un `FileContext`.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> crée des instances de `IFileContextAction`.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> Exporte le type `IWorkspaceProviderFactory<IFileContextActionProvider>`.

## <a name="file-watching"></a>Surveillance du fichier

Un espace de travail à l’écoute des notifications de modification de fichier et fournit le <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> via <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. Fichiers correspond au paramètre « Eléments exclus » ne produira pas les événements de notification de fichier. Un seuil entre les événements est utilisé pour la simplification de la notification et de réduction en double. Lorsque vous avez besoin réagir à une modification de fichier, vous devez vous abonner à ce service.

>[!TIP]
>Un espace de travail [service d’indexation](workspace-indexing.md) s’abonne aux événements de fichier par défaut. Ajouts de fichiers et des modifications entraîne pertinentes `IFileScanner`événements s à appeler pour les nouvelles données pour ce fichier. Suppressions de fichiers supprimera les données indexées. Vous n’avez pas besoin de s’abonner votre `IFileScanner` au service de l’Observateur de fichier.

## <a name="next-steps"></a>Étapes suivantes

* [L’indexation](workspace-indexing.md) -espace de travail d’indexation collecte et conserve des informations sur l’espace de travail.
* [Espaces de travail](workspaces.md) -passez en revue les concepts de l’espace de travail et de stockage des paramètres.
