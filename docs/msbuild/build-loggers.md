---
title: "Enregistreurs d’événements de génération | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
caps.latest.revision: 11
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b28a3a7d7412a496802a176f6365e961cd7c2673
ms.lasthandoff: 02/22/2017

---
# <a name="build-loggers"></a>Enregistreurs d’événements de génération
Les enregistreurs d’événements vous permettent de personnaliser la sortie de votre génération et d’afficher des messages, des erreurs ou des avertissements en réponse à des événements de génération spécifiques. Chaque enregistreur d’événements est implémenté en tant que classe .NET qui implémente l’interface <xref:Microsoft.Build.Framework.ILogger>, qui est définie dans l’assembly Microsoft.Build.Framework.dll.  
  
 Vous pouvez adopter deux approches lors de l’implémentation d’un enregistreur d’événements :  
  
-   Implémenter directement l’interface <xref:Microsoft.Build.Framework.ILogger>.  
  
-   Dériver votre classe de la classe d’assistance, <xref:Microsoft.Build.Utilities.Logger>, qui est définie dans l’assembly Microsoft.Build.Utilities.dll. <xref:Microsoft.Build.Utilities.Logger> implémente <xref:Microsoft.Build.Framework.ILogger> et fournit des implémentations par défaut de certains membres <xref:Microsoft.Build.Framework.ILogger>.  
  
 Cette rubrique explique comment écrire un enregistreur d’événements simple qui dérive de <xref:Microsoft.Build.Utilities.Logger> et affiche des messages dans la console en réponse à certains événements de génération.  
  
## <a name="registering-for-events"></a>Inscription pour des événements  
 L’objectif d’un enregistreur d’événements consiste à rassembler des informations sur la progression de la génération telles que signalées par le moteur de génération, puis à signaler ces informations de manière utile. Tous les enregistreurs d’événements doivent substituer la méthode <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>, qui est l’emplacement où l’enregistreur d’événements s’inscrit pour des événements. Dans cet exemple, l’enregistreur d’événements s’inscrit pour les événements <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> et <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.  
  
 [!code-cs[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]  
  
## <a name="responding-to-events"></a>Réponse aux événements  
 Maintenant que l’enregistreur d’événements est inscrit pour des événements spécifiques, il doit gérer ces événements quand ils se produisent. Pour les événements <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> et <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>, l’enregistreur d’événements écrit simplement une courte expression et le nom du fichier projet impliqué dans l’événement. Tous les messages de l’enregistreur d’événements sont écrits dans la fenêtre de console.  
  
 [!code-cs[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]  
  
## <a name="responding-to-logger-verbosity-values"></a>Réponse aux valeurs Verbosity de l’enregistreur d’événements  
 Dans certains cas, vous souhaiterez enregistrer les informations d’un événement uniquement si le commutateur **/verbosity** de MSBuild.exe contient une certaine valeur. Dans cet exemple, le Gestionnaire d’événements <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> enregistre un message uniquement si la propriété <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A>, qui est définie par le commutateur **/verbosity**, est égale à <xref:Microsoft.Build.Framework.LoggerVerbosity>`Detailed`.  
  
 [!code-cs[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]  
  
## <a name="specifying-a-logger"></a>Spécification d’un enregistreur d’événements  
 Une fois l’enregistreur d’événements compilé dans un assembly, vous devez indiquer à [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] qu’il faut utiliser cet enregistreur d’événements pendant les générations. Pour cela, vous devez utiliser le commutateur **/logger** avec MSBuild.exe. Pour plus d’informations sur les commutateurs disponibles pour MSBuild.exe, consultez [Référence de ligne de commande](../msbuild/msbuild-command-line-reference.md).  
  
 La ligne de commande suivante génère le projet `MyProject.csproj` et utilise la classe d’enregistreur d’événements implémentée dans `SimpleLogger.dll`. Le commutateur **/nologo** masque la bannière et le message de copyright, et le commutateur **/noconsolelogger** désactive l’enregistreur d’événements de console [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] par défaut.  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll  
```  
  
 La ligne de commande suivante génère le projet avec le même enregistreur d’événements, mais avec un niveau `Verbosity` égal à `Detailed`.  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll /verbosity:Detailed  
```  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant contient le code complet pour l’enregistreur d’événements.  
  
### <a name="code"></a>Code  
 [!code-cs[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]  
  
### <a name="comments"></a>Commentaires  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant montre comment implémenter un enregistreur d’événements qui écrit le journal dans un fichier au lieu de l’afficher dans la fenêtre de console.  
  
### <a name="code"></a>Code  
 [!code-cs[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]  
  
### <a name="comments"></a>Commentaires  
  
## <a name="see-also"></a>Voir aussi  
 [Obtention de journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Concepts MSBuild](../msbuild/msbuild-concepts.md)
