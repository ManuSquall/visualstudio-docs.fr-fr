---
title: "L’installation du Kit de développement logiciel Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8a5a4721eea178e4a9ab5766760ccf1405589684
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="installing-the-visual-studio-sdk"></a>Installer le Kit de développement logiciel de Visual Studio
Le Kit de développement logiciel Visual Studio est une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS ultérieurement.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>L’installation du Kit de développement logiciel Visual Studio en tant que partie d’une Installation de Visual Studio  
 Si vous souhaitez inclure l’extensibilité de Visual Studio dans votre installation de Visual Studio, vous devez installer le **le développement d’extensions Visual Studio** la charge de travail sous **des ensembles d’outils autres**. Cela installe le Kit de développement logiciel Visual Studio, ainsi que les conditions préalables. Vous pouvez affiner l’installation en sélectionnant ou désélectionnant les composants à partir du résumé afficher. 
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>L’installation du Kit de développement logiciel Visual Studio après l’installation de Visual Studio  
 Si vous décidez d’installer le Kit de développement logiciel Visual Studio après avoir effectué votre installation de Visual Studio, réexécutez le programme d’installation de Visual Studio et sélectionnez le **le développement d’extensions Visual Studio** la charge de travail.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>L’installation de Visual Studio SDK à partir d’une Solution  
 Si vous ouvrez une solution avec un projet d’extensibilité sans d’abord installer l’extensibilité de Visual Studio, vous êtes invité par une barre d’informations en surbrillance au-dessus de l’Explorateur de solutions. Il doit se présenter comme suit :  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>L’installation de Visual Studio SDK à partir de la ligne de commande  
Comme avec une charge de travail de Visual Studio ou un composant, vous pouvez également installer l’élément à partir de la ligne de commande. Consultez [utiliser les paramètres de ligne de commande pour installer Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) pour plus d’informations sur les commutateurs de ligne de commande appropriée et comment déterminer les identificateurs de charge de travail ou un composant.
  
 Notez que vous devez utiliser le programme d’installation de Visual Studio qui correspond à votre version installée de Visual Studio. Par exemple, si vous avez Visual Studio Enterprise est installé sur votre ordinateur, vous devez exécuter le programme d’installation de Visual Studio Enterprise (vs_enterprise.exe).