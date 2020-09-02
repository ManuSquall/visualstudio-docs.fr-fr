---
title: 'Comment : Rechercher le nom du processus ASP.NET | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 53072013c1665687262d30f4a0c2720641c920be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685955"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>Comment : rechercher le nom du processus ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour créer un attachement à une application [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] en cours d'exécution, vous devez connaître le nom du processus [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] :  
  
- Si vous exécutez IIS 6.0 ou IIS 7.0, le nom est w3wp.exe.  
  
- Si vous exécutez une version antérieure d'IIS, le nom est aspnet_wp.exe.  
  
  Pour les applications générées à l’aide de [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] ou versions ultérieures, le [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] code peut résider sur le système de fichiers et s’exécuter sous le serveur de test WebDev.WebServer.exe. Dans ce cas, vous devez créer un attachement à WebDev.WebServer.exe au lieu du processus [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Ce scénario s'applique uniquement au débogage local.  
  
  Les applications antérieures d'ASP s'exécutent à l'intérieur du processus IIS inetinfo.exe lorsqu'elles s'exécutent in-process.  
  
> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition. Pour modifier vos paramètres, choisissez **Paramètres d'importation et d'exportation** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-determine-whether-project-code-resides-on-the-file-system-or-iis"></a>Pour déterminer si le code de projet réside sur le système de fichiers ou IIS  
  
1. Dans Visual Studio, ouvrez **Explorateur de solutions** s’il n’est pas déjà ouvert.  
  
2. Sélectionnez le nœud supérieur qui contient le nom de l'application.  
  
3. Si le titre de la fenêtre **Propriétés** contient un chemin d’accès au fichier, le code de l’application réside sur le système de fichiers.  
  
     Dans le cas contraire, le titre de la fenêtre **Propriétés** contiendra le nom du site Web.  
  
### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>Pour déterminer la version d'IIS sous laquelle l'application s'exécute  
  
1. Recherchez les **Outils d’administration** et exécutez-le. Selon votre système d’exploitation, il peut s’agir d’une icône dans **le panneau de configuration**ou d’une entrée de menu qui s’affiche lorsque vous cliquez sur **Démarrer**.  
  
     Dans Windows XP, **le panneau de configuration** peut être en affichage des catégories ou en affichage classique. Dans l’affichage des catégories, vous devez cliquer sur **basculer vers l’affichage classique** ou sur **performances et maintenance** pour afficher l’icône **Outils d’administration** .  
  
2. Dans **Outils d’administration**, exécutez Internet Information Services. Une boîte de dialogue MMC apparaît.  
  
3. Si plusieurs ordinateurs sont répertoriés dans le volet gauche, sélectionnez celui sur lequel réside le code de l'application.  
  
4. La version d’IIS se trouve dans la colonne **version** du volet droit.  
  
## <a name="see-also"></a>Voir aussi  
 [Prérequis pour le débogage distant d’applications Web](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Configuration système requise](../debugger/aspnet-debugging-system-requirements.md)   
 [Préparation du débogage de ASP.NET](../debugger/preparing-to-debug-aspnet.md)   
 [Débogage d'applications et de scripts Web](../debugger/debugging-web-applications-and-script.md)
