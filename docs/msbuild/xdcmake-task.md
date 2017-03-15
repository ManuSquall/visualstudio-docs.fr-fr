---
title: "XDCMake Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.xdcmake"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "XDCMake task (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), XDCMake task"
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# XDCMake Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Encapsule l'outil de documentation XML \(xdcmake.exe\), qui fusionne des fichiers du commentaire \(.xdc\) du document XML dans un fichier .xml.  
  
 Un fichier .xdc est créé lorsque vous fournissez des commentaires sur la documentation dans votre code source de Visual C\+\+ et compilez en utilisant l'option de compilateur [\/doc](/visual-cpp/build/reference/doc-process-documentation-comments-c-cpp).  Pour plus d'informations, consultez [Référence XDCMake](/visual-cpp/ide/xdcmake-reference), [Outil Générateur de documents XML, page de propriétés](/visual-cpp/ide/xml-document-generator-tool-property-pages) et l'option de l'aide de la ligne de commande \(**\/?**\) pour xdcmake.exe.  
  
## Notes  
 Par défaut, l'outil xdcmake.exe prend en charge quelques options de ligne de commande.  Des options supplémentaires sont prises en charge lorsque vous spécifiez l'option de ligne de commande **\/old**.  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche **XDCMake**.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|Paramètre **String\[\]** facultatif.<br /><br /> Spécifie un ou plusieurs fichiers .xdc supplémentaires à fusionner.<br /><br /> Pour plus d'informations, consultez la description **Fichiers de document supplémentaires** dans [Outil Générateur de documents XML, page de propriétés](/visual-cpp/ide/xml-document-generator-tool-property-pages).  Consultez également les options de ligne de commande **\/old** et **\/Fs** pour xdcmake.exe.|  
|**AdditionalOptions**|Paramètre **String** facultatif.<br /><br /> Une liste d'options comme spécifié sur la ligne de commande.  Par exemple, "*\/option1 \/option2 \/option\#*".  Utilisez ce paramètre pour spécifier des options qui ne sont pas représentées par un autre paramètre de tâche **XDCMake**.<br /><br /> Pour plus d'informations, consultez [Référence XDCMake](/visual-cpp/ide/xdcmake-reference), [Outil Générateur de documents XML, page de propriétés](/visual-cpp/ide/xml-document-generator-tool-property-pages), et l'aide de la ligne de commande \(**\/?**\) pour xdcmake.exe.|  
|**DocumentLibraryDependencies**|Paramètre **Boolean** facultatif.<br /><br /> Si `true` et le projet actuel a une dépendance sur un projet de bibliothèque statique \(.lib\) dans la solution, les fichiers .xdc pour ce projet de bibliothèque sont inclus dans la sortie de fichier .xml pour le projet actuel.<br /><br /> Pour plus d'informations, consultez la description **Dépendances de bibliothèque de documents** dans [Outil Générateur de documents XML, page de propriétés](/visual-cpp/ide/xml-document-generator-tool-property-pages).|  
|**OutputFile**|Paramètre **String** facultatif.<br /><br /> Substitue le nom de fichier de sortie par défaut.  Le nom par défaut est dérivé du nom du premier fichier .xdc traité.<br /><br /> Pour plus d'informations, consultez l'option **\/out:**`filename` dans [Référence XDCMake](/visual-cpp/ide/xdcmake-reference).  Consultez également les options de ligne de commande **\/old** et **\/Fo** pour xdcmake.exe.|  
|**ProjectName**|Paramètre **String** facultatif.<br /><br /> Nom du projet actif.|  
|**SlashOld**|Paramètre **Boolean** facultatif.<br /><br /> Si `true`, active des options xdcmake.exe supplémentaires.<br /><br /> Pour plus d'informations, consultez l'option de ligne de commande **\/old** pour xdcmake.exe.|  
|**Sources**|Paramètre `ITaskItem[]` obligatoire.<br /><br /> Définit un tableau des éléments de fichier source MSBuild qui peuvent être consommés et peuvent être émis par les tâches.|  
|**SuppressStartupBanner**|Paramètre **Boolean** facultatif.<br /><br /> Si `true`, empêche l'affichage du copyright et du numéro de version lorsque la tâche démarre.<br /><br /> Pour plus d'informations, consultez l'option **\/nologo** dans [Référence XDCMake](/visual-cpp/ide/xdcmake-reference).|  
|**TrackerLogDirectory**|Paramètre **String** facultatif.<br /><br /> Spécifie le répertoire correspondant au journal de Tracker.|  
  
## Voir aussi  
 [Task Reference](../msbuild/msbuild-task-reference.md)