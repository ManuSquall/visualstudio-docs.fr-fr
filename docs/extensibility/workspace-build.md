---
title: Build d’espace de travail dans Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 82660ee772280563b91830aaf1a18da0bc742b28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62553326"
---
# <a name="workspace-build"></a>Création de l’espace de travail

La prise en charge des builds dans les scénarios [ouverts](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) requiert un extendeur pour fournir des données d' [index](workspace-indexing.md) et de [contexte de fichier](workspace-file-contexts.md) pour l' [espace de travail](workspaces.md), ainsi que l’action de génération à exécuter.

Vous trouverez ci-dessous un aperçu des besoins de votre extension.

## <a name="build-file-context"></a>Contexte de fichier de build

- Fabrique de fournisseurs
  - `ExportFileContextProviderAttribute` attribut avec `supportedContextTypeGuids` toutes les `string` constantes applicables à partir de `BuildContextTypes`
  - Implémente `IWorkspaceProviderFactory<IFileContextProvider>`
  - Fournisseur de contexte de fichier
    - Retourner une `FileContext` pour chaque opération de génération et la configuration prise en charge
      - `contextType` à partir de <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` implémente <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> avec la `Configuration` propriété comme configuration de build (par exemple `"Debug|x86"` , `"ret"` ou `null` si non applicable). Vous pouvez également utiliser une instance de <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext> . La valeur de configuration **doit** correspondre à la configuration de la valeur de données de fichier indexée.

## <a name="indexed-build-file-data-value"></a>Valeur des données du fichier de build indexé

- Fabrique de fournisseurs
  - `ExportFileScannerAttribute` attribut avec `IReadOnlyCollection<FileDataValue>` comme type pris en charge
  - Implémente `IWorkspaceProviderFactory<IFileScanner>`
- Analyseur de fichiers activé `ScanContentAsync<T>`
  - Retourne des données lorsque `FileScannerTypeConstants.FileDataValuesType` est l’argument de type
  - Retourne une valeur de données de fichier pour chaque configuration construite avec :
    - `type` servir `BuildConfigurationContext.ContextTypeGuid`
    - `context` comme configuration de build (par exemple `"Debug|x86"` , `"ret"` ou `null` si non applicable). Cette valeur **doit** correspondre à la configuration du contexte de fichier.

## <a name="build-file-context-action"></a>Action de contexte de fichier de build

- Fabrique de fournisseurs
  - `ExportFileContextActionProvider` attribut avec `supportedContextTypeGuids` toutes les `string` constantes applicables à partir de `BuildContextTypes`
  - Implémente `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Fournisseur d’actions sur `IFileContextActionProvider.GetActionsAsync`
  - Retourne un `IFileContextAction` qui correspond à la `FileContext.ContextType` valeur donnée.
- Action de contexte de fichier
  - Implémente `IFileContextAction` et <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` retourne la propriété `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` est `0x1000` pour la génération, `0x1010` pour la régénération ou `0x1020` pour le nettoyage

>[!NOTE]
>Étant donné que le `FileDataValue` doit être indexé, il y aura un laps de temps entre l’ouverture de l’espace de travail et le point auquel le fichier est analysé pour la fonctionnalité de génération complète. Le délai sera visible lors de la première ouverture d’un dossier, car il n’y a pas d’index précédemment mis en cache.

## <a name="reporting-messages-from-a-build"></a>Création de rapports de messages à partir d’une build

La build peut exposer des informations, des avertissements et des messages d’erreur aux utilisateurs de deux manières. Le moyen le plus simple consiste à utiliser <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> et à fournir un <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage> , comme suit :

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Build;

private static void OutputBuildMessage(IWorkspace workspace)
{
    IBuildMessageService buildMessageService = workspace.GetBuildMessageService();

    if (buildMessageService != null)
    {
      // Example error build message. See the documentation for BuildMessage for more information.
      var message = new BuildMessage()
      {
          Type = BuildMessage.TaskType.Error,
          Code = "MY1001",
          TaskText = "This is a sample error",
          ProjectFile = "buildfile.bld",
          File = "sourcefile.src"
          LogMessage = $"This is sample text that will only go to the Build output window pane.\n"

          // And any other properties to set
      };

      buildMessageService.ReportBuildMessages(new BuildMessage[] { message });
    }
}
```

`BuildMessage.Type` et `BuildMessage.LogMessage` contrôler le comportement de l’emplacement où les informations sont présentées à l’utilisateur. Toute `BuildMessage.TaskType` valeur autre que produira `None` une entrée de **liste d’erreurs** avec les détails donnés. `LogMessage` sera toujours sortie dans le volet de **génération** de la fenêtre outil de **sortie** .

Les extensions peuvent également interagir directement avec le volet de **liste d’erreurs** ou de **Build** . Il existe un bogue dans les versions antérieures à Visual Studio 2017 version 15,7, où l' `pszProjectUniqueName` argument de <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> est ignoré.

>[!WARNING]
>Les appelants de `IFileContextAction.ExecuteAsync` peuvent fournir des implémentations sous-jacentes arbitraires pour l' `IProgress<IFileContextActionProgressUpdate>` argument. N’appelez jamais `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` directement. Il n’existe actuellement aucune instruction générale pour l’utilisation de cet argument, mais ces recommandations sont sujettes à modification.

## <a name="build-related-apis"></a>API associées à la Build

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> fournit des détails sur la configuration de Build.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> affiche <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage> les utilisateurs.

## <a name="tasksvsjson-and-launchvsjson"></a>tasks.vs.jssur et launch.vs.js

Pour plus d’informations sur la création d’un tasks.vs.jssur le fichier ou sur launch.vs.js, consultez [personnaliser les tâches de génération et de débogage](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Étapes suivantes

* [Protocole du serveur de langage](language-server-protocol.md) : Découvrez comment intégrer des serveurs de langue dans Visual Studio.