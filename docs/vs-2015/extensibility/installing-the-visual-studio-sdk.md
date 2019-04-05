---
title: Installer le SDK Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: visual-studio-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 796d5f3f233310157b0784e213b81237e767055b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951682"
---
# <a name="installing-the-visual-studio-sdk"></a>Installer le SDK Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Installer le SDK Visual Studio en tant que partie d’une Installation de Visual Studio  
 Si vous souhaitez inclure l’extensibilité Visual Studio dans votre installation de Visual Studio, vous devez effectuer une installation personnalisée.  
  
> [!NOTE]
>  Dans l’exécutable d’installation, le SDK Visual Studio est appelé **outils d’extensibilité Visual Studio**.  
  
1.  Démarrez l’installation de Visual Studio 2015. Vous pouvez installer n’importe quelle édition de Visual Studio sauf Express.  
  
2.  Dans le premier écran, sélectionnez **personnalisé**, et non **par défaut**. Cliquez sur **Suivant**.  
  
3.  Vous devez voir une arborescence de fonctionnalités personnalisées. Ouvrez **outils courants**. Vous devriez voir **outils d’extensibilité Visual Studio** .  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4.  Vérifiez **outils d’extensibilité Visual Studio** , puis cliquez sur **suivant** et poursuivre l’installation.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Installer le SDK Visual Studio après l’installation de Visual Studio  
 Si vous décidez d’installer le SDK Visual Studio après avoir effectué votre installation de Visual Studio, vous devez suivre la procédure suivante :  
  
1.  Accédez à **le panneau de configuration / programmes / programmes et fonctionnalités**, puis recherchez **Visual Studio 2015**. Vous pouvez installer le SDK Visual Studio pour n’importe quelle édition de Visual Studio 2015, à l’exception d’Express.  
  
2.  Avec le bouton droit **Visual Studio 2015**, puis cliquez sur **modification**. Vous devez voir la page d’installation.  
  
3.  Suivez la même procédure que dans **l’installation du Kit de développement logiciel Visual Studio en tant que partie d’une Installation de Visual Studio** ci-dessus.  
  
4.  Cliquez sur le **outils d’extensibilité Visual Studio** lien pour installer le SDK Visual Studio.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Installer le SDK Visual Studio à partir d’une Solution  
 Si vous ouvrez une solution avec un projet d’extensibilité sans d’abord installer l’extensibilité de Visual Studio, vous êtes invité par une barre d’informations en surbrillance au-dessus de l’Explorateur de solutions. Il doit ressembler à ce qui suit :  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Installer le SDK Visual Studio à partir de la ligne de commande  
 Vous pouvez installer l’extensibilité Visual Studio à partir de la ligne de commande en utilisant le **/installselectableitems.** commutateur avec le programme d’installation de Visual Studio. Pour plus d’informations sur l’utilisation de paramètres de ligne de commande avec le programme d’installation, consultez [l’installation de Visual Studio 2015](../install/install-visual-studio-2015.md).  
  
 Voici comment installer l’extensibilité de Visual Studio en mode silencieux à l’aide du programme d’installation de Visual Studio 2015 Community :  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Notez que vous devez utiliser le programme d’installation de Visual Studio qui correspond à votre version installée de Visual Studio. Par exemple, si vous avez Visual Studio Enterprise est installé sur votre ordinateur, vous devez exécuter le programme d’installation de Visual Studio Enterprise (vs_enterprise.exe).
