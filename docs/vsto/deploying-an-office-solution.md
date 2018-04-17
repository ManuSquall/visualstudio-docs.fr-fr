---
title: Déploiement d’une Solution Office | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office applications [Office development in Visual Studio], deploying Office solutions
- Office development in Visual Studio, deploying Office solutions
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- deploying applications [Office development in Visual Studio], Office solutions (2007 system)
- Office development in Visual Studio, troubleshooting
- Office development in Visual Studio, event viewer
- ClickOnce deployment [Office development in Visual Studio], about ClickOnce solution deployments
- Office solutions [Office development in Visual Studio], deploying
- deploying applications [Office development in Visual Studio], troubleshooting
- solutions [Office development in Visual Studio], deploying Office solutions (2007 system)
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1a397ef0986bd2a278f4b341dc772c71bc9b0a51
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="deploying-an-office-solution"></a>Déploiement d'une solution Office
  Vous pouvez déployer des solutions Office à l'aide des technologies de déploiement ClickOnce ou Windows Installer. En utilisant ClickOnce, vous réduisez le nombre d'étapes que nécessitent le déploiement et la mise à jour de votre solution. Si vous utilisez Windows Installer, vous pouvez contrôler la manière dont une solution est installée et les pages du programme d'installation qui s'affichent lorsque les utilisateurs installent votre solution.  
  
> [!NOTE]  
>  Vous souhaitez développer des solutions qui étendent l’expérience Office sur [plusieurs plateformes](https://dev.office.com/add-in-availability)? Découvrez le nouvel [modèle des compléments Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Compléments Office ont un faible encombrement mémoire par rapport aux compléments VSTO et les solutions, et vous pouvez les créer à l’aide de presque n’importe quel web technologies, telles que HTML5, JavaScript, CSS3 et XML de programmation.  
  
## <a name="deploying-a-solution-by-using-clickonce"></a>Déploiement d'une solution en utilisant ClickOnce  
 Lorsque vous déployez une solution en utilisant ClickOnce, vous la publiez dans un emplacement central où les utilisateurs peuvent l'installer et l'exécuter. Vous pouvez mettre à jour la solution sans avoir à distribuer un nouveau programme d'installation aux utilisateurs.  Cette option de déploiement est plus simple, mais vous ne pouvez pas afficher de pages d'installation personnalisées pour les utilisateurs. En outre, les solutions doivent être installées plusieurs fois sur un ordinateur ayant plusieurs utilisateurs. Consultez [déploiement d’une Solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="deploying-a-solution-by-using-windows-installer"></a>Déploiement d'une solution à l'aide de Windows Installer  
 Lorsque vous déployez une solution à l'aide de Windows Installer, vous devez distribuer un programme d'installation aux utilisateurs afin qu'ils installent la solution. Le programme d'installation peut installer une solution pour tous les utilisateurs d'un ordinateur en même temps, plutôt que l'utilisateur actuel uniquement. Vous avez également un peu plus de contrôle sur les options proposées aux utilisateurs lors de l'installation de votre solution. Par exemple, vous pouvez afficher un contrat de licence ou permettre aux utilisateurs d'installer les composants spécifiques d'une solution. Toutefois, si vous mettez à jour la solution, vous devez distribuer le programme d'installation. Consultez [déploiement d’une Solution Office à l’aide de Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation des Solutions Office](../vsto/securing-office-solutions.md)   
 [Déploiement d’une Solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Déploiement d’une Solution Office à l’aide de Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md)   
 [Dépannage du déploiement de solutions Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  