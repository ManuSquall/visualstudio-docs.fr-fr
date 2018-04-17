---
title: Génération d’espace de travail dans Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 813f7a5e-f298-4469-9f4c-a5bddf5a6e14
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: f7415c99c68436519f9bab721fe88a48f750fa1c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="workspace-build"></a>Génération de l’espace de travail

Générez la prise en charge dans [ouvrir le dossier](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) scénarios requiert un extendeur pour fournir [indexée](workspace-indexing.md) et [de contexte du fichier](workspace-file-contexts.md) les données de la [espace de travail](workspaces.md), en tant que ainsi que l’action de génération à exécuter.

Voici un plan de besoins votre extension.

## <a name="build-file-context"></a>Générer le contexte du fichier

- Fabrique de fournisseurs
  - `ExportFileContextProviderAttribute` attribut `supportedContextTypeGuids` applicable que tous les `string` constantes à partir de `BuildContextTypes`
  - Implémente `IWorkspaceProviderFactory<IFileContextProvider>`
  - Fournisseur de contexte de fichier
    - Retourner un `FileContext` pour chaque build configuration prise en charge et du fonctionnement
      - `contextType` De <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` implémente <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> avec la `Configuration` propriété en tant que la configuration de build (par exemple `"Debug|x86"`, `"ret"`, ou `null` si non applicable). Vous pouvez également utiliser une instance de <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext>. La valeur de configuration **doit** correspond à la configuration de la valeur de données de fichiers indexés.

## <a name="indexed-build-file-data-value"></a>Valeur de données de fichier indexée de build

- Fabrique de fournisseurs
  - `ExportFileScannerAttribute` attribut avec `IReadOnlyCollection<FileDataValue>` comme un type pris en charge
  - Implémente `IWorkspaceProviderFactory<IFileScanner>`
- Analyseur de fichiers sur `ScanContentAsync<T>`
  - Retourne des données lorsque `FileScannerTypeConstants.FileDataValuesType` est l’argument de type
  - Retourne une valeur de données de fichier pour chaque configuration construite avec :
    - `type` en tant que `BuildConfigurationContext.ContextTypeGuid`
    - `context` en tant que votre configuration de build (par exemple `"Debug|x86"`, `"ret"`, ou `null` si non applicable). Cette valeur **doit** correspond à la configuration à partir du contexte du fichier.

## <a name="build-file-context-action"></a>Fichier contexte action de génération

- Fabrique de fournisseurs
  - `ExportFileContextActionProvider` attribut `supportedContextTypeGuids` applicable que tous les `string` constantes à partir de `BuildContextTypes`
  - Implémente `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Fournisseur d’actions sur `IFileContextActionProvider.GetActionsAsync`
  - Retourner un `IFileContextAction` qui correspond à la donnée `FileContext.ContextType` valeur
- Action de contexte de fichiers
  - Implémente `IFileContextAction` et <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` retourne de propriété `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` est `0x1000` pour la build, `0x1010` de reconstruction, ou `0x1020` pour nettoyer

>[!NOTE]
>Étant donné que le `FileDataValue` doit être indexée, il y aura une certaine quantité de temps entre l’ouverture de l’espace de travail et le point auquel le fichier est analysé pour la fonctionnalité de génération complète. Le délai d’attente s’affiche sur la première ouverture d’un dossier, car il n’existe aucun index précédemment mise en cache.

## <a name="reporting-messages-from-a-build"></a>Messages de création de rapports à partir d’une build

La build peut apparaître plus d’informations, d’avertissement et messages d’erreur pour les utilisateurs de deux manières. La simple consiste à utiliser le <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> et fournir un <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>, comme suit :

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

`BuildMessage.Type` et `BuildMessage.LogMessage` contrôler le comportement d’où les informations sont présentées à l’utilisateur. N’importe quel `BuildMessage.TaskType` valeur autre que `None` produira une **liste d’erreurs** entrée avec les détails donnés. `LogMessage` affichera toujours dans le **générer** volet de la **sortie** fenêtre outil.

Vous pouvez également les extensions peuvent interagir directement avec le **liste d’erreurs** ou **générer** volet. Il existe un bogue dans les versions antérieures de Visual Studio 2017 Version 15.7 où le `pszProjectUniqueName` argument de <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> est ignoré.

>[!WARNING]
>Les appelants de `IFileContextAction.ExecuteAsync` peut fournir des implémentations sous-jacentes arbitraires pour le `IProgress<IFileContextActionProgressUpdate>` argument. Ne jamais appeler `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` directement. Il n’y a actuellement aucun règles générales pour l’utilisation de cet argument, mais ces recommandations sont susceptibles de changer.

## <a name="build-related-apis"></a>API associées à la build

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> Fournit des détails de configuration de build.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> montre <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>s pour les utilisateurs.

## <a name="tasksvsjson-and-launchvsjson"></a>Tasks.VS.JSON et launch.vs.json

Pour plus d’informations sur la création d’un fichier tasks.vs.json ou launch.vs.json, consultez [personnaliser la génération et débogage des tâches](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Étapes suivantes

* [Protocole de serveur de langage](language-server-protocol.md) -Apprenez à intégrer des serveurs de langage dans Visual Studio.