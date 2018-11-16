---
title: 'Comment : déboguer une partie non exécutable d’une Solution Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a7fb9b0a31f078ce197851bccb1f4c85f24408a0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798662"
---
# <a name="how-to-debug-an-executable-not-part-of-a-visual-studio-solution"></a>Comment : déboguer un fichier exécutable ne faisant pas partie d'une solution Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez être amené à déboguer un exécutable qui ne fait pas partie d'un projet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Il peut s'agir d'un exécutable créé en dehors de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ou reçu de la part d'un tiers.  
  
 La réponse usuelle à ce problème consiste à démarrer l'exécutable en dehors de Visual Studio, puis à l'attacher à l'aide du débogueur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Pour plus d’informations, consultez [Attacher aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 L'attachement à une application requiert quelques étapes manuelles, qui prennent tout de même quelques secondes. Ce léger décalage peut rendre l'attachement inutile si vous essayez de déboguer un problème survenant au démarrage. De même, si vous déboguez un programme qui n'attend aucune entrée d'utilisateur et se termine rapidement, vous risquez de ne pas avoir le temps de l'attacher. Si [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] est installé, vous pouvez créer un projet EXE pour un tel programme.  
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>Pour créer un projet EXE pour un exécutable existant  
  
1.  Dans le menu **Fichier**, cliquez sur **Ouvrir** et sélectionnez **Projet**.  
  
2.  Dans la boîte de dialogue **Ouvrir un projet**, cliquez sur la liste déroulante située à côté de la zone **Nom du fichier**, puis sélectionnez **Tous les fichiers du projet**.  
  
3.  Localiser le fichier exécutable, puis cliquez sur **OK**.  
  
     Cela permet de créer une solution temporaire contenant l'exécutable.  
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>Pour importer un exécutable dans une solution Visual Studio  
  
1.  Dans le menu **Fichier**, pointez sur **Ajouter un projet**, puis cliquez sur **Projet existant**.  
  
2.  Dans la boîte de dialogue **Ajouter un projet existant**, cliquez sur la liste déroulante située à côté de la zone **Nom du fichier**, puis sélectionnez **Tous les fichiers du projet**.  
  
3.  Recherchez et sélectionnez l'exécutable.  
  
4.  Cliquez sur **OK**.  
  
5.  Démarrez l’exécutable en choisissant une commande d’exécution, telle que **Démarrer**, à partir du menu **Déboguer**.  
  
    > [!NOTE]
    >  Tous les langages de programmation ne prennent pas en charge les projets EXE. Installez [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] si vous devez utiliser cette fonctionnalité.  
  
     Lorsque vous déboguez un exécutable sans le code source, les fonctionnalités de débogage disponibles sont limitées, que vous attachiez l'exécutable en cours d'exécution ou que vous l'ajoutiez à une solution [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Si l'exécutable a été généré sans informations de débogage dans un format compatible, les fonctionnalités disponibles sont encore plus limitées. Si vous disposez du code source, la meilleure approche consiste à l'importer dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour y créer une version Debug de l'exécutable [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Fichiers DBG](http://msdn.microsoft.com/en-us/91e449e9-8b65-4123-960f-2107cd1f1cfd)



