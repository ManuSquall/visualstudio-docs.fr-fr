---
title: Prise en main de Visual Studio Graphics Diagnostics | Documents Microsoft
ms.custom: 
ms.date: 05/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59131181-1caa-4b7f-be4b-e84709634edf
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 36045b311a73af96df51553f9025a1de84c93b78
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Prise en main de Visual Studio Graphics Diagnostics
Dans cette section, vous allez vous préparer à utiliser Graphics Diagnostics pour la première fois, puis vous allez capturer des frames à partir d’une application Direct3D et les examiner dans Graphics Analyzer.  
  
## <a name="requirements"></a>Configuration requise  
 Pour utiliser Graphics Diagnostics dans Visual Studio, vous devez utiliser Visual Studio Enterprise, Visual Studio Professional ou Visual Studio Community.  Autres éditions, y compris le Code de Visual Studio, ne contiennent pas cette fonctionnalité.
 
 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]  
  
### <a name="windows-10-prerequisites"></a>Composants requis pour Windows 10  
 La fonctionnalité Windows facultative *outils graphiques* fournit l’infrastructure de capture et de lecture nécessaire à Graphics Diagnostics sur Windows 10.  
  
 Pour plus d’informations sur l’installation des outils graphiques, consultez [installer Graphics outils pour Windows 10](#InstallGraphicsTools).  
  
### <a name="windows-81-prerequisites"></a>Composants requis pour Windows 8.1  
 Le Kit de développement logiciel (SDK) Windows pour Windows 8.1 fournit l’infrastructure de capture et de lecture nécessaire à Graphics Diagnostics sur Windows 8.1. En outre, il prend en charge le développement pour Windows 8.1 et Windows 8.  
  
 [Télécharger le Kit de développement de logiciel (SDK) Windows pour Windows 8.1](https://msdn.microsoft.com/en-us/windows/desktop/bg162891.aspx)  
  
 Pour utiliser un ordinateur de lecture distant qui exécute Windows 10 à partir d’un ordinateur de développement exécutant Windows 8.1, vous devez installer le Kit de développement logiciel (SDK) Windows 10 sur l’ordinateur de développement et la fonctionnalité facultative Outils Graphics sur l’ordinateur de lecture.  
  
##  <a name="InstallGraphicsTools"></a>Installer les outils Graphics pour Windows 10  
 Dans Windows 10, l’infrastructure Graphics Diagnostics est fournie par une fonctionnalité facultative de Windows appelée *outils graphiques*. Cette fonctionnalité est nécessaire pour capturer et lire les informations graphiques sur Windows 10, indépendamment du fait que l’application capturée cible ou non une version antérieure de Windows, ou indépendamment de la version de Direct3D utilisée. Vous pouvez choisir d’installer la fonctionnalité Outils Graphics à l’avance. Sinon, elle est installée à la demande la première fois que vous démarrez une session Graphics Diagnostics à partir de Visual Studio.  
  
#### <a name="to-install-graphics-tools-for-windows-10"></a>Pour installer Outils Graphics pour Windows 10  
  
1.  Dans Rechercher, tapez **applications et fonctionnalités** , puis ouvrez le **applications & fonctionnalités** paramètres.
  
3.  Sur le côté droit de la **applications & fonctionnalités** boîte de dialogue, choisissez **gérer les fonctionnalités facultatives** (sous **applications & fonctionnalités**).

    Le **gérer les fonctionnalités facultatives** boîte de dialogue s’affiche.
  
4.  Dans le **gérer les fonctionnalités facultatives** boîte de dialogue, choisissez **ajouter une fonctionnalité**. Une liste de fonctionnalités facultatives que vous pouvez installer s’affiche.  
  
5.  Sélectionnez **outils graphiques** dans la liste des fonctionnalités, puis choisissez **installer**.  
  
 La fonctionnalité Outils Graphics est également installée automatiquement quand vous installez le Kit de développement logiciel (SDK) Windows 10.  
  
> [!TIP]
>  La fonctionnalité facultative outils Graphics de Windows 10 fournit des fonctionnalités légères de capture et de lecture, tels que le programme de capture de ligne de commande **dxcap.exe**, qui peut être utilisé dans la prise en charge, le test et des scénarios de diagnostic sur ordinateurs sur lesquels les outils de développement ne sont pas installés. Pour plus d’informations, consultez la [outil de Capture de ligne de commande](command-line-capture-tool.md) rubrique.  
  
## <a name="using-graphics-diagnostics-for-the-first-time"></a>Utilisation de Graphics Diagnostics pour la première fois  
 Une fois que vous avez tout ce dont vous avez besoin, vous êtes prêt à utiliser Graphics Diagnostics. Procédez comme suit :  
  
### <a name="1---create-a-direct3d-app"></a>1 - Créer une application Direct3D  
 Si vous avez déjà votre propre application Direct3D pour Explorer Graphics Diagnostics, c’est parfait ! Sinon, utilisez une des opérations suivantes :

- Le **DirectX 11 application (Windows universel)** ou **DirectX 12 application (Windows universel)** modèles de projet pour Windows 10.
- Le **l’application DirectX (Windows 8.1)** modèle de projet pour Windows 8.1.
- [Exemple Direct3D 12 UAP](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) pour Windows 10.  
- Le [exemple de jeu DirectX marble maze](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345) pour Windows 8.1.  
  
 Assurez-vous que vous pouvez générer l'application avant de continuer.  
  
### <a name="2---start-a-graphics-diagnostics-session"></a>2 - Démarrer une session Graphics Diagnostics  
 Maintenant, vous êtes prêt à démarrer votre première session Graphics Diagnostics. Dans Visual Studio, dans le menu principal, choisissez **déboguer, graphiques, démarrer le débogage graphique**, ou appuyez simplement sur **Alt + F5**. Cela entraîne le démarrage de votre application dans Graphics Diagnostics et l’affichage des fenêtres de session de diagnostic dans Visual Studio.  
  
> [!IMPORTANT]
>  Si vous exécutez votre application sur Windows 10 et si vous n’avez pas encore installé la fonctionnalité facultative Outils Graphics, vous êtes invité à le faire maintenant. Vous devez l’installer avant de pouvoir utiliser Graphics Diagnostics sur Windows 10.  
  
### <a name="3---capture-frames"></a>3 - Capturer des frames  
 Vous êtes prêt à capturer des frames dès le démarrage de votre application.  
  
#### <a name="to-capture-single-frames"></a>Pour capturer des frames uniques  
  
-   Dans Visual Studio, choisissez le **capturer le Frame** bouton à partir de la fenêtre de session de diagnostic ou de la barre d’outils graphiques. Ou, si votre application a le focus, appuyez sur la **Impr. écran** clé de votre clavier.
  
#### <a name="to-capture-a-sequence-of-frames"></a>Pour capturer une séquence de frames  
  
-   Dans Visual Studio, dans la fenêtre de la session de diagnostic, définissez **Frames à capturer** au nombre de frames à capturer dans la séquence, puis capturez la séquence en utilisant l’une des méthodes ci-dessus pour capturer des frames uniques.  
  
     Pour capturer des frames uniques à nouveau, définissez **Frames à capturer** à *1*.  
  
 Lorsque vous avez terminé capturer les frames juste quitter l’application ou choisissez la **arrêter** le bouton de la barre d’outils graphiques ou de la fenêtre de la session de diagnostic.  
  
### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4 - examiner les frames capturés dans Graphics Analyzer  
 À présent, vous êtes prêt à examiner les frames que vous venez de capturer. Pour démarrer l'analyse d'un frame, choisissez le numéro du frame que vous souhaitez examiner à partir de la fenêtre de session de diagnostic. S’ouvre dans le cadre de la **Graphics Analyzer**, où vous pouvez utiliser les outils Graphics Diagnostics pour examiner la façon dont votre application utilise Direct3D pour détecter les problèmes de rendu, ou utiliser le **analyse des frames** outil pour comprendre ses performances.  
  
 Si vous avez sélectionné le mauvais frame dans la fenêtre de session de diagnostic, ou si vous souhaitez examiner un autre frame, vous pouvez en sélectionner un nouveau dans Graphics Analyzer. Sur le **restituer la cible** onglet de la fenêtre de journal de graphisme, sous l’image de cible de rendu, développez le **liste de frames** , puis choisissez un autre frame à examiner.  
  
 Pour en savoir plus sur l’utilisation des outils Graphics Analyzer, consultez le [exemples](graphics-diagnostics-examples.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Direct3D 12 Graphics](http://msdn.microsoft.com/en-us/52094ae3-3b44-4689-9ee7-1ba1b3a779cb)