---
title: Installation du kit de développement logiciel (SDK) Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: visual-studio-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88a6266a3f5910def0bf5041a37f89c2b3d67416
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840254"
---
# <a name="installing-the-visual-studio-sdk"></a>Installation du Kit de développement logiciel (SDK) Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Installation du kit de développement logiciel (SDK) Visual Studio dans le cadre d’une installation de Visual Studio  
 Si vous souhaitez inclure le VSSDK dans votre installation de Visual Studio, vous devez effectuer une installation personnalisée.  
  
> [!NOTE]
> Dans l’exécutable d’installation, le kit de développement logiciel (SDK) Visual Studio est appelé **Outils d’extensibilité de Visual Studio**.  
  
1. Démarrez l’installation de Visual Studio 2015. Vous pouvez installer n’importe quelle édition de Visual Studio, à l’exception de Express.  
  
2. Dans le premier écran, sélectionnez **personnalisé**, et non **par défaut**. Cliquez sur **Suivant**.  
  
3. Une arborescence de fonctionnalités personnalisées doit s’afficher. Ouvrez **outils courants**. Vous devez voir **Outils d’extensibilité de Visual Studio** .  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4. Cochez **Outils d’extensibilité de Visual Studio** , puis cliquez sur **suivant** et poursuivez l’installation.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Installation du kit de développement logiciel (SDK) Visual Studio après l’installation de Visual Studio  
 Si vous décidez d’installer le kit de développement logiciel (SDK) Visual Studio après avoir terminé l’installation de Visual Studio, vous devez suivre la procédure suivante :  
  
1. Accédez à **panneau de configuration/programmes/programmes et fonctionnalités**et recherchez **Visual Studio 2015**. Vous pouvez installer le kit de développement logiciel (SDK) Visual Studio pour n’importe quelle édition de Visual Studio 2015, à l’exception de Express.  
  
2. Cliquez avec le bouton droit sur **Visual Studio 2015**, puis cliquez sur **modifier**. La page d’installation doit s’afficher.  
  
3. Suivez la même procédure que pour l' **installation du kit de développement logiciel (SDK) Visual Studio dans le cadre d’une installation de Visual Studio** ci-dessus.  
  
4. Cliquez sur le lien **Outils d’extensibilité de Visual Studio** pour installer le kit de développement logiciel (SDK) Visual Studio.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Installation du kit de développement logiciel (SDK) Visual Studio à partir d’une solution  
 Si vous ouvrez une solution avec un projet d’extensibilité sans installer au préalable le VSSDK, vous serez invité par une barre d’informations en surbrillance au-dessus de la Explorateur de solutions. La commande doit ressembler à ceci :  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Installation du kit de développement logiciel (SDK) Visual Studio à partir de la ligne de commande  
 Vous pouvez installer VSSDK à partir de la ligne de commande à l’aide du commutateur **/InstallSelectableItems** avec le programme d’installation de Visual Studio. Pour plus d’informations sur l’utilisation des paramètres de ligne de commande avec le programme d’installation, consultez [installation de Visual Studio 2015](../install/install-visual-studio-2015.md).  
  
 Voici comment installer le VSSDK en mode silencieux à l’aide du programme d’installation de la Communauté Visual Studio 2015 :  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Notez que vous devez utiliser le programme d’installation de Visual Studio qui correspond à la version installée de Visual Studio. Par exemple, si vous avez Visual Studio Enterprise installé sur votre ordinateur, vous devez exécuter le programme d’installation Visual Studio Enterprise (vs_enterprise.exe).
