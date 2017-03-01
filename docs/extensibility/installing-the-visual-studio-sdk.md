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
ms.sourcegitcommit: 9c25532605613b34ded15a4bd6a533e589b7fce2
ms.openlocfilehash: d039c50cea2ee038baec26fad02a98ae45f0d521
ms.lasthandoff: 02/22/2017

---
# <a name="installing-the-visual-studio-sdk"></a>L’installation du Kit de développement logiciel de Visual Studio
À partir de Visual Studio 2015, vous n’installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>L’installation du Kit de développement logiciel de Visual Studio en tant que partie d’une Installation de Visual Studio  
 Si vous souhaitez inclure VSSDK dans votre installation de Visual Studio, vous devez effectuer une installation personnalisée.  
  
> [!NOTE]
>  Dans l’exécutable d’installation, le Kit de développement Visual Studio est appelé **outils d’extensibilité de Visual Studio**.  
  
1.  Démarrez l’installation de Visual Studio 2015. Vous pouvez installer n’importe quelle édition de Visual Studio, à l’exception d’Express.  
  
2.  Dans le premier écran, sélectionnez **personnalisé**, et non pas **par défaut**. Cliquez sur **Next**.  
  
3.  Vous devez voir une arborescence des fonctionnalités personnalisées. Ouvrez **outils communs**. Vous devez voir **outils d’extensibilité de Visual Studio** .  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4.  Vérifiez **d’extensibilité de Visual Studio Tools** , puis cliquez sur **suivant** et poursuivre l’installation.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>L’installation du Kit de développement logiciel de Visual Studio après l’installation de Visual Studio  
 Si vous décidez d’installer le Kit de développement logiciel Visual Studio après avoir terminé votre installation de Visual Studio, vous devez suivre la procédure suivante :  
  
1.  Accédez à **le panneau de configuration / programmes / programmes et fonctionnalités**, puis recherchez **Visual Studio 2015**. Vous pouvez installer le SDK de Visual Studio pour n’importe quelle édition de Visual Studio 2015, à l’exception d’Express.  
  
2.  Avec le bouton droit **Visual Studio 2015**, puis cliquez sur **modification**. Vous devez voir la page d’installation.  
  
3.  Suivez la même procédure que dans **l’installation du Kit de développement logiciel Visual Studio en tant que partie d’une Installation de Visual Studio** ci-dessus.  
  
4.  Cliquez sur le **d’extensibilité de Visual Studio Tools** lien pour installer le Kit de développement Visual Studio.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>L’installation du Kit de développement logiciel de Visual Studio à partir d’une Solution  
 Si vous ouvrez une solution avec un projet d’extensibilité sans d’abord installer VSSDK, vous êtes invité par une barre d’informations en surbrillance au-dessus de l’Explorateur de solutions. Il doit se présenter comme suit :  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>L’installation du Kit de développement logiciel de Visual Studio à partir de la ligne de commande  
 Vous pouvez installer VSSDK à partir de la ligne de commande à l’aide de la **/InstallSelectableItems** commutateur avec le programme d’installation de Visual Studio. Pour plus d’informations sur l’utilisation de paramètres de ligne de commande avec le programme d’installation, consultez la page [utiliser des paramètres de ligne de commande pour installer Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md).  
  
 Voici comment installer en mode silencieux à l’aide du programme d’installation de Visual Studio 2015 Community VSSDK :  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Notez que vous devez utiliser le programme d’installation de Visual Studio qui correspond à la version installée de Visual Studio. Par exemple, si vous avez Visual Studio Enterprise est installé sur votre ordinateur, vous devez exécuter le programme d’installation de Visual Studio Enterprise (vs_enterprise.exe).
