---
title: "L’installation du Kit de développement logiciel de Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- visual-studio-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 722c32c139d2f560fa6d10aba9fd8bac610f9f20
ms.lasthandoff: 03/07/2017

---
# <a name="installing-the-visual-studio-sdk"></a>L’installation du Kit de développement logiciel de Visual Studio
Le Kit de développement Visual Studio est une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>L’installation du Kit de développement logiciel de Visual Studio en tant que partie d’une Installation de Visual Studio  
 Si vous souhaitez inclure VSSDK dans votre installation de Visual Studio, vous devez installer le **le développement d’extensions Visual Studio** la charge de travail sous **autres ensembles d’outils**. Cette commande installe le Kit de développement Visual Studio, ainsi que les conditions préalables requises. Vous pouvez affiner l’installation en sélectionnant ou désélectionnant des composants à partir du résumé (affichage). 
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>L’installation du Kit de développement logiciel de Visual Studio après l’installation de Visual Studio  
 Si vous décidez d’installer le Kit de développement logiciel Visual Studio après avoir terminé votre installation de Visual Studio, réexécutez le programme d’installation de Visual Studio, puis sélectionnez le **le développement d’extensions Visual Studio** la charge de travail.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>L’installation du Kit de développement logiciel de Visual Studio à partir d’une Solution  
 Si vous ouvrez une solution avec un projet d’extensibilité sans d’abord installer VSSDK, vous êtes invité par une barre d’informations en surbrillance au-dessus de l’Explorateur de solutions. Il doit se présenter comme suit :  
  
 ![SolutionExplorerInstall](~/extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>L’installation du Kit de développement logiciel de Visual Studio à partir de la ligne de commande  
Comme avec une charge de travail de Visual Studio ou un composant, vous pouvez également installer l’élément à partir de la ligne de commande. Consultez la page [utiliser des paramètres de ligne de commande pour installer Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) pour plus d’informations sur les commutateurs de ligne de commande appropriée et comment déterminer les identificateurs de charge de travail ou d’un composant.
  
 Notez que vous devez utiliser le programme d’installation de Visual Studio qui correspond à la version installée de Visual Studio. Par exemple, si vous avez Visual Studio Enterprise est installé sur votre ordinateur, vous devez exécuter le programme d’installation de Visual Studio Enterprise (vs_enterprise.exe).
