---
title: Déployer une solution Office
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d0040ee123c88d2cd54b96701523a5a28fd03b64
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872389"
---
# <a name="deploy-an-office-solution"></a>Déployer une solution Office
  Vous pouvez déployer des solutions Office à l'aide des technologies de déploiement ClickOnce ou Windows Installer. En utilisant ClickOnce, vous réduisez le nombre d'étapes que nécessitent le déploiement et la mise à jour de votre solution. Si vous utilisez Windows Installer, vous pouvez contrôler la manière dont une solution est installée et les pages du programme d'installation qui s'affichent lorsque les utilisateurs installent votre solution.  
  
> [!NOTE]  
>  Vous souhaitez développer des solutions qui étendent l’expérience Office sur [plusieurs plateformes](https://dev.office.com/add-in-availability)? Découvrez le nouvel [modèle de compléments Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Compléments Office peu encombrantes par rapport aux compléments VSTO et de solutions, et vous pouvez les créer à l’aide de presque toutes les technologies, telles que HTML5, JavaScript, CSS3 et XML de programmation web.  
  
## <a name="deploy-a-solution-by-using-clickonce"></a>Déployer une solution à l’aide de ClickOnce  
 Lorsque vous déployez une solution en utilisant ClickOnce, vous la publiez dans un emplacement central où les utilisateurs peuvent l'installer et l'exécuter. Vous pouvez mettre à jour la solution sans avoir à distribuer un nouveau programme d'installation aux utilisateurs.  Cette option de déploiement est plus simple, mais vous ne pouvez pas afficher de pages d'installation personnalisées pour les utilisateurs. En outre, les solutions doivent être installées plusieurs fois sur un ordinateur ayant plusieurs utilisateurs. Consultez [déployer une solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="deploy-a-solution-by-using-windows-installer"></a>Déployer une solution à l’aide du programme d’installation de Windows  
 Lorsque vous déployez une solution à l'aide de Windows Installer, vous devez distribuer un programme d'installation aux utilisateurs afin qu'ils installent la solution. Le programme d'installation peut installer une solution pour tous les utilisateurs d'un ordinateur en même temps, plutôt que l'utilisateur actuel uniquement. Vous avez également un peu plus de contrôle sur les options proposées aux utilisateurs lors de l'installation de votre solution. Par exemple, vous pouvez afficher un contrat de licence ou permettre aux utilisateurs d'installer les composants spécifiques d'une solution. Toutefois, si vous mettez à jour la solution, vous devez distribuer le programme d'installation. Consultez [déployer une solution Office à l’aide du programme d’installation de Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisez les solutions Office](../vsto/securing-office-solutions.md)   
 [Déployer une solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Déployer une solution Office à l’aide du programme d’installation de Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md)   
 [Résoudre les problèmes de déploiement de solutions Office](../vsto/troubleshooting-office-solution-deployment.md)  
