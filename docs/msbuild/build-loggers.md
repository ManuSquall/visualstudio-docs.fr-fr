---
title: Enregistreurs d’événements de génération | Microsoft Docs
description: Utilisez les enregistreurs d’événements MSBuild pour gérer et personnaliser la sortie de votre génération et afficher des messages, des erreurs ou des avertissements en réponse à des événements de build spécifiques.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c56de103fa116cbf77ec16dc0116a2897e6ccdce
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92353198"
---
# <a name="build-loggers"></a>Enregistreurs d’événements de génération

Les enregistreurs d’événements vous permettent de personnaliser la sortie de votre génération et d’afficher des messages, des erreurs ou des avertissements en réponse à des événements de génération spécifiques. Chaque enregistreur d’événements est implémenté en tant que classe .NET qui met en œuvre l’interface <xref:Microsoft.Build.Framework.ILogger>, définie dans l’assembly *Microsoft.Build.Framework.dll*.

Vous pouvez adopter deux approches lors de l’implémentation d’un enregistreur d’événements :

- implémenter directement l’interface <xref:Microsoft.Build.Framework.ILogger> ;
- dériver votre classe de la classe d’assistance, <xref:Microsoft.Build.Utilities.Logger>, définie dans l’assembly *Microsoft.Build.Utilities.dll*. <xref:Microsoft.Build.Utilities.Logger> implémente <xref:Microsoft.Build.Framework.ILogger> et fournit des implémentations par défaut de certains membres <xref:Microsoft.Build.Framework.ILogger>.

  Cette rubrique explique comment écrire un enregistreur d’événements simple qui dérive de <xref:Microsoft.Build.Utilities.Logger> et affiche des messages sur la console en réponse à certains événements de build.

## <a name="register-for-events"></a>S’inscrire aux événements

L’objectif d’un enregistreur d’événements consiste à rassembler des informations sur la progression de la génération telles que signalées par le moteur de génération, puis à signaler ces informations de manière utile. Tous les enregistreurs d’événements doivent substituer la méthode <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>, où l’enregistreur d’événements enregistre les événements. Dans cet exemple, l’enregistreur d’événements enregistre les événements <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> et <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.

[!code-csharp[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]

## <a name="respond-to-events"></a>Répondre aux événements

Maintenant que l’enregistreur d’événements est inscrit pour des événements spécifiques, il doit gérer ces événements quand ils se produisent. Pour les événements <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> et <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>, l’enregistreur d’événements écrit simplement une courte expression et le nom du fichier projet impliqué dans l’événement. Tous les messages de l’enregistreur d’événements sont écrits dans la fenêtre de console.

[!code-csharp[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]

## <a name="respond-to-logger-verbosity-values"></a>Répondre aux valeurs de détails de l’enregistreur d’événements

Dans certains cas, vous souhaiterez peut-être enregistrer uniquement les informations d’un événement si le commutateur MSBuild.exe **-verbosity** contient une certaine valeur. Dans cet exemple, le <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> Gestionnaire d’événements enregistre un message uniquement si la <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A> propriété, définie par le commutateur **-verbosity** , est égale à <xref:Microsoft.Build.Framework.LoggerVerbosity> `Detailed` .

[!code-csharp[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]

## <a name="specify-a-logger"></a>Spécifier un enregistreur d’événements

Une fois l’enregistreur d’événements compilé dans un assembly, vous devez indiquer à MSBuild d’utiliser cet enregistreur d’événements pendant les builds. Pour ce faire, utilisez le commutateur **-logger** avec *MSBuild.exe*. Pour plus d’informations sur les commutateurs disponibles pour *MSBuild.exe*, consultez [Informations de référence sur la ligne de commande](../msbuild/msbuild-command-line-reference.md).

La ligne de commande suivante génère le projet *MyProject.csproj* et utilise la classe d’enregistreur d’événements implémentée dans *SimpleLogger.dll*. Le commutateur **-nologo** masque la bannière et le message de copyright, et le commutateur **-noconsolelogger** désactive l’enregistreur d’événements de console MSBuild par défaut.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll
```

La ligne de commande suivante génère le projet avec le même enregistreur d’événements, mais avec un niveau `Verbosity` égal à `Detailed`.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll -verbosity:Detailed
```

## <a name="example-1"></a>Exemple 1

### <a name="description"></a>Description

L’exemple suivant contient le code complet pour l’enregistreur d’événements.

### <a name="code"></a>Code

[!code-csharp[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]

## <a name="example-2"></a>Exemple 2

### <a name="description"></a>Description

L’exemple suivant montre comment implémenter un enregistreur d’événements qui écrit le journal dans un fichier au lieu de l’afficher dans la fenêtre de console.

### <a name="code"></a>Code

[!code-csharp[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]

## <a name="see-also"></a>Voir aussi

- [Obtenir des journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Concepts MSBuild](../msbuild/msbuild-concepts.md)
