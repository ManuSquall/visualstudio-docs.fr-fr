---
title: 'Comment : déboguer un exécutable qui ne fait pas partie d’une solution Visual Studio | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e16a938eda683a607dbf7d9418b2a7bd4455a0da
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-debug-an-executable-that-is-not-part-of-a-visual-studio-solution"></a>Comment : déboguer un exécutable qui ne fait pas partie d’une solution Visual Studio
Vous pouvez être amené à déboguer un exécutable (fichier .exe) qui n’est pas dans le cadre d’un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet. Il peut s'agir d'un exécutable créé en dehors de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou reçu de la part d'un tiers.  
  
La réponse usuelle à ce problème consiste à démarrer l'exécutable en dehors de Visual Studio, puis à l'attacher à l'aide du débogueur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pour plus d’informations, consultez [attacher au processus en cours](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
L'attachement à une application requiert quelques étapes manuelles, qui prennent tout de même quelques secondes. Ce léger décalage peut rendre l'attachement inutile si vous essayez de déboguer un problème survenant au démarrage. De même, si vous déboguez un programme qui n'attend aucune entrée d'utilisateur et se termine rapidement, vous risquez de ne pas avoir le temps de l'attacher. Si vous avez [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] et [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] , vous pouvez créer un projet EXE pour un tel programme.

> [!NOTE]
>  Tous les langages de programmation ne prennent pas en charge les projets EXE.

Lorsque vous déboguez un exécutable qui ne fait pas partie de votre solution Visual Studio, les fonctionnalités de débogage disponibles peuvent être limitées, que vous attachez à un fichier exécutable en cours d’exécution ou d’ajoutez l’exécutable à un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solution.

- Si vous disposez du code source, la meilleure approche consiste à l'importer dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour y créer une version Debug de l'exécutable[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].
- Si vous n’avez pas le code source, et si le fichier exécutable a été généré sans [les informations de débogage](../debugger/how-to-set-debug-and-release-configurations.md) dans un format compatible, les fonctionnalités de débogage disponibles sont très limitées. 
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>Pour créer un projet EXE pour un exécutable existant  
  
1.  Sur le **fichier** menu, cliquez sur **ouvrir** et sélectionnez **projet**.  
  
2.  Dans le **ouvrir le projet** boîte de dialogue, cliquez sur la liste en regard de la liste déroulante le **nom de fichier** et sélectionnez **tous les fichiers projet**.  
  
3.  Localiser le fichier exécutable, puis cliquez sur **OK**.  

    Cela permet de créer une solution temporaire contenant l'exécutable.

5.  Démarrer l’exécutable en choisissant une commande d’exécution, telles que **Démarrer**, à partir de la **déboguer** menu.    
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>Pour importer un exécutable dans une solution Visual Studio  
  
1.  Sur le **fichier** menu, pointez sur **ajouter un projet**, puis cliquez sur **projet existant**.  
  
2.  Dans le **ajouter un projet existant** boîte de dialogue, cliquez sur la liste en regard de la liste déroulante le **nom de fichier** et sélectionnez **tous les fichiers projet**.  
  
3.  Recherchez et sélectionnez l'exécutable.  
  
4.  Cliquez sur **OK**.  
  
5.  Démarrer l’exécutable en choisissant une commande d’exécution, telles que **Démarrer**, à partir de la **déboguer** menu.    
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Fichiers DBG](http://msdn.microsoft.com/en-us/91e449e9-8b65-4123-960f-2107cd1f1cfd)