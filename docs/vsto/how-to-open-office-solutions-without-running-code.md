---
title: 'Comment : ouvrir des Solutions Office sans exécuter du Code | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 86a44d2a6c82f65d91c558c76743a8fbbd2fa1e8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Comment : ouvrir des solutions Office sans exécuter le code
  Une solution Microsoft Office créée avec les extensions de code managé s’exécute même si le paramètre de sécurité dans l’application Office de l’utilisateur final est élevé. Il s’agit, car la sécurité du code assembly .NET est gérée par Microsoft .NET Framework, et non par Microsoft Office.  
  
 Toutefois, il existe des heures lorsque vous souhaiterez ouvrir un document sans exécuter le code. Par exemple, le contenu susceptible de modifier le code qui s’exécute lorsque le document s’ouvre, mais vous souhaitez mettre à jour de l’apparence du document avant les modifications de code il. Ou vous souhaiterez peut-être envoyer le document avec certaines informations dans celui-ci à quelqu'un, et vous ne souhaitez pas que le code à exécuter et éventuellement modifier le contenu.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Il existe plusieurs façons d’ouvrir un document ou classeur qui contient des extensions de code managé sans exécuter le code de l’assembly.  
  
### <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Pour ignorer l’assembly à l’aide de la touche MAJ ENFONCÉE  
  
-   Ouvrir des documents et classeurs à partir de la **fichier** menu tout en maintenant enfoncée la touche MAJ pour empêcher le déclenchement d’événements d’initialisation lors de l’ouverture des documents Word et Excel.  
  
    > [!NOTE]  
    >  Si vous ouvrez un document ou classeur à partir de la **mise en route** volet de tâches, maintenez la touche MAJ n’ignore pas le code. En outre, maintenez la touche MAJ n’empêche pas d’événements de déclenché une fois que le document est ouvert.  
  
     Cette méthode est utile si vous souhaitez ouvrir un document pour apporter des modifications sans le code en cours d’exécution et modification d’abord le document.  
  
### <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Pour ignorer un assembly en renommant ou en supprimant  
  
-   Si vous avez les autorisations nécessaires sur l’ordinateur où se trouve l’assembly, vous pouvez renommer ou supprimer l’assembly afin que le document ou le classeur ne peut pas le trouver. Cela entraîne une erreur qui est déclenchée chaque fois que le document Office est ouvert.  
  
     Si la solution est utilisée par plusieurs personnes, cette méthode empêche la solution en cours d’exécution pour chacun d’eux. Cela peut être utile si un problème est détecté dans le code ou un serveur référencé et que vous souhaitez arrêter tous les utilisateurs de l’exécuter.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation des Solutions Office](../vsto/securing-office-solutions.md)   
 [Déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md)   
 [Conception et création de Solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Manifestes d’application et de déploiement dans les solutions Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  