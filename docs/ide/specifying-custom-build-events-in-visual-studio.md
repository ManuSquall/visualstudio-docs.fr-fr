---
title: "Spécification d’événements de build personnalisés dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
caps.latest.revision: 13
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 8c4bd89d533e535769e74baf31ab102788585bc9
ms.contentlocale: fr-fr
ms.lasthandoff: 05/13/2017

---
# <a name="specifying-custom-build-events-in-visual-studio"></a>Spécification d'événements de build personnalisés dans Visual Studio
En spécifiant un événement de build personnalisé, vous pouvez automatiquement exécuter des commandes avant le démarrage d'une build ou quand elle est terminée. Par exemple, vous pouvez exécuter un fichier .bat avant qu'une build ne démarre ou copier de nouveaux fichiers dans un dossier une fois la build terminée. Les événements de build ne s'exécutent que si la build atteint ces étapes du processus de génération.  
  
 Pour obtenir des informations spécifiques sur le langage de programmation que vous utilisez, consultez les rubriques suivantes :  
  
-   Visual Basic--[Guide pratique pour spécifier des événements de build (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).  
  
-   Visual C# et F#--[Guide pratique pour spécifier des événements de build (C#)](../ide/how-to-specify-build-events-csharp.md).  
  
-   Visual C++--[Spécifications d’événements de build](/cpp/ide/specifying-build-events).  
  
## <a name="syntax"></a>Syntaxe  
 Les événements de build suivent la même syntaxe que les commandes DOS, mais vous pouvez utiliser des macros pour créer plus facilement des événements de build. Pour obtenir la liste des macros disponibles, consultez [Ligne de commande de l’événement pré-build/post-build, boîte de dialogue](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).  
  
 Pour de meilleurs résultats, suivez ces conseils de mise en forme :  
  
-   Ajouter une instruction `call` avant tous les événements de build qui exécutent des fichiers .bat.  
  
     Exemple : `call C:\MyFile.bat`  
  
     Exemple : `call C:\MyFile.bat call C:\MyFile2.bat`  
  
-   Placez les chemins d'accès de fichier entre guillemets.  
  
     Exemple (pour [!INCLUDE[win8](../debugger/includes/win8_md.md)]) : "%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe" -if "$(TargetPath)"  
  
-   Séparez les commandes à l'aide de sauts de ligne.  
  
-   Incluez des caractères génériques si nécessaire.  
  
     Exemple : `for %I in (*.txt *.doc *.html) do copy %I c:\`*mon_répertoire*`\`  
  
    > [!NOTE]
    >  `%I` dans le code ci-dessus doit être `%%I` dans les scripts de commandes.  
  
## <a name="see-also"></a>Voir aussi  
 [Compilation et génération](../ide/compiling-and-building-in-visual-studio.md)   
 [Ligne de commande de l’événement pré-build/post-build, boîte de dialogue](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [Caractères spéciaux MSBuild](../msbuild/msbuild-special-characters.md)   
 [Procédure pas à pas : génération d’une application](../ide/walkthrough-building-an-application.md)
