---
title: Prise en main avec Graphics Diagnostics | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 59131181-1caa-4b7f-be4b-e84709634edf
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e9056fdae9d0eff55c572d8e38503d88269dbde3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704705"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Prise en main de Visual Studio Graphics Diagnostics
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans cette section, vous allez vous préparer à utiliser Graphics Diagnostics pour la première fois, puis vous allez capturer des frames à partir d’une application Direct3D et les examiner dans Graphics Analyzer.

## <a name="requirements"></a>Configuration requise
 Pour utiliser Graphics Diagnostics dans Visual Studio 2015, vous devez avoir l’une de ces éditions :

- Visual Studio Enterprise 2015

- Visual Studio Professional 2015

- Visual Studio Community 2015

  [!INCLUDE[downloadvs](../includes/downloadvs-md.md)]

### <a name="windows-10-prerequisites"></a>Prérequis pour Windows 10
 La fonctionnalité Windows facultative *Outils Graphics* fournit l’infrastructure de capture et de lecture nécessaire à Graphics Diagnostics sur Windows 10.

 Pour plus d’informations sur l’installation de la fonctionnalité Outils Graphics, consultez [Installer Outils Graphics pour Windows 10](#InstallGraphicsTools).

### <a name="windows-81-prerequisites"></a>Composants requis pour Windows 8.1
 Le Kit de développement logiciel (SDK) Windows pour Windows 8.1 fournit l'infrastructure de capture et de lecture nécessaire à Graphics Diagnostics sur Windows 8.1. En outre, il prend en charge le développement pour Windows 8.1 et Windows 8.

 [Téléchargez le kit de développement logiciel (SDK) Windows pour Windows 8.1](https://msdn.microsoft.com/windows/desktop/bg162891.aspx)

 Pour utiliser un ordinateur de lecture distant qui exécute Windows 10 à partir d’un ordinateur de développement exécutant Windows 8.1, vous devez installer le Kit de développement logiciel (SDK) Windows 10 sur l’ordinateur de développement et la fonctionnalité facultative Outils Graphics sur l’ordinateur de lecture.

## <a name="install-graphics-tools-for-windows-10"></a><a name="InstallGraphicsTools"></a> Installer Outils Graphics pour Windows 10
 Dans Windows 10, l’infrastructure Graphics Diagnostics est fournie par une fonctionnalité facultative de Windows appelée *Outils Graphics*. Cette fonctionnalité est nécessaire pour capturer et lire les informations graphiques sur Windows 10, indépendamment du fait que l'application capturée cible ou non une version antérieure de Windows, ou indépendamment de la version de Direct3D utilisée. Vous pouvez choisir d'installer la fonctionnalité Outils Graphics à l'avance. Sinon, elle est installée à la demande la première fois que vous démarrez une session Graphics Diagnostics à partir de Visual Studio.

#### <a name="to-install-graphics-tools-for-windows-10"></a>Pour installer Outils Graphics pour Windows 10

1. Dans le menu **Démarrer** , choisissez **paramètres**. La boîte de dialogue **paramètres** s’affiche.

2. Dans la boîte de dialogue **paramètres** , choisissez **système**, puis sélectionnez **applications installées** dans la liste des paramètres système.

3. Sur le côté droit de la boîte de dialogue **paramètres** , choisissez **gérer les fonctionnalités facultatives** sous **applications et fonctionnalités installées**. La boîte de dialogue **Gérer les fonctionnalités facultatives** s’affiche.

4. Dans la boîte de dialogue **Gérer les fonctionnalités facultatives**, choisissez **Ajouter une fonctionnalité**. Une liste de fonctionnalités facultatives que vous pouvez installer s'affiche.

5. Sélectionnez **Outils Graphics** dans la liste des fonctionnalités, puis choisissez **Installer**.

   La fonctionnalité Outils Graphics est également installée automatiquement quand vous installez le Kit de développement logiciel (SDK) Windows 10.

> [!TIP]
> La fonctionnalité facultative Outils Graphics de Windows 10 fournit des fonctionnalités légères de capture et de lecture (telles que le programme en ligne de commande de capture **dxcap.exe**) qui peuvent être utilisées dans les scénarios de prise en charge, de test et de diagnostic sur les ordinateurs où les outils de développement ne sont pas installés. Pour plus d’informations, consultez la rubrique [Outil en ligne de commande de capture](../debugger/command-line-capture-tool.md).

## <a name="using-graphics-diagnostics-for-the-first-time"></a>Utilisation de Graphics Diagnostics pour la première fois
 Une fois que vous avez tout ce dont vous avez besoin, vous êtes prêt à utiliser Graphics Diagnostics. Suivez simplement cette procédure.

### <a name="1---create-a-direct3d-app"></a>1 - Créer une application Direct3D
 Si vous avez déjà votre propre application Direct3D pour explorer Graphics Diagnostics, c'est parfait ! Sinon, vous pouvez utiliser l'un des exemples Direct3D disponibles dans la galerie de code.

- Pour tester Graphics Diagnostics avec Direct3D 12 sur Windows 10 à l’aide de Visual Studio 2015, essayez l’exemple de l' [UAP Direct3D 12](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) pour Windows 10.

- Pour tester Graphics Diagnostics avec Direct3D 11 sur Windows 10 ou Windows 8.1, vous pouvez utiliser les modèles de projet **application DirectX (Windows universel)** ou  **application DirectX (Windows 8.1)** . Pour obtenir des informations plus intéressantes, essayez l' [exemple de jeu de labyrinthe DirectX Marble](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345) pour Windows 8.1.

  Assurez-vous que vous pouvez générer l'application avant de continuer.

### <a name="2---start-a-graphics-diagnostics-session"></a>2 - Démarrer une session Graphics Diagnostics
 Maintenant, vous êtes prêt à démarrer votre première session Graphics Diagnostics. Dans Visual Studio, dans le menu principal, choisissez **Déboguer, graphiques, démarrer les diagnostics**ou appuyez simplement sur **Alt + F5**. Cela entraîne le démarrage de votre application dans Graphics Diagnostics et l’affichage des fenêtres de session de diagnostic dans Visual Studio.

> [!IMPORTANT]
> Si vous exécutez votre application sur Windows 10 et si vous n'avez pas encore installé la fonctionnalité facultative Outils Graphics, vous êtes invité à le faire maintenant. Vous devez l’installer avant de pouvoir utiliser Graphics Diagnostics sur Windows 10.

### <a name="3---capture-frames"></a>3 - Capturer des frames
 Vous êtes prêt à capturer des frames dès le démarrage de votre application.

##### <a name="to-capture-single-frames"></a>Pour capturer des frames uniques

- Dans Visual Studio, choisissez le bouton **Capturer le frame** à partir de la barre d’outils Graphics ou de la fenêtre de session de diagnostic. Ou, si votre application a le focus, appuyez simplement sur **Impr. écran**.

##### <a name="to-capture-a-sequence-of-frames"></a>Pour capturer une séquence de frames

- Dans Visual Studio, dans la fenêtre de session de diagnostic, affectez à **Nombre de frames à capturer** le nombre de frames à capturer dans la séquence, puis capturez la séquence en utilisant l’une des méthodes ci-dessus pour capturer des frames uniques.

   Pour capturer à nouveau des frames uniques, définissez les **frames à capturer** `1` .

  Une fois que vous avez fini de capturer les frames, quittez simplement l’application, ou choisissez le bouton **Arrêter** dans la barre d’outils Graphics ou la fenêtre de session de diagnostic.

### <a name="4--examine-captured-frames-in-the-graphics-analyzer"></a>4 - Examiner les frames capturés dans Graphics Analyzer
 À présent, vous êtes prêt à examiner les frames que vous venez de capturer. Pour démarrer l'analyse d'un frame, choisissez le numéro du frame que vous souhaitez examiner à partir de la fenêtre de session de diagnostic. Cela entraîne l’ouverture du frame dans **Graphics Analyzer**, où vous pouvez soit utiliser les outils Graphics Diagnostics pour examiner la façon dont votre application utilise Direct3D pour détecter les problèmes de rendu, soit utiliser l’outil **Analyse des frames** pour comprendre ses performances.

 Si vous avez sélectionné le mauvais frame dans la fenêtre de session de diagnostic, ou si vous souhaitez examiner un autre frame, vous pouvez en sélectionner un nouveau dans Graphics Analyzer. Sous l’onglet **Restituer la cible** de la fenêtre du journal de graphisme, sous l’image de la cible de rendu, développez la **Liste de frames**, puis choisissez un autre frame à examiner.

 Pour en savoir plus sur l’utilisation conjointe des outils Graphics Analyzer, consultez les [exemples](../debugger/graphics-diagnostics-examples.md).

## <a name="see-also"></a>Voir aussi
 [Graphiques Direct3D 12](https://msdn.microsoft.com/52094ae3-3b44-4689-9ee7-1ba1b3a779cb)
