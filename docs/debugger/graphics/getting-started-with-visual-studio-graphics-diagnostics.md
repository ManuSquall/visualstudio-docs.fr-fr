---
title: Prise en main de Graphics Diagnostics | Microsoft Docs
description: Préparez-vous à utiliser Graphics Diagnostics pour la première fois, puis capturer des frames à partir d’une application Direct3D et les examiner dans Graphics Analyzer.
ms.custom: SEO-VS-2020
ms.date: 06/08/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 70512b4df3be7f11973af244c336b22c59c90f8f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387604"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Prise en main de Visual Studio Graphics Diagnostics
Dans cette section, vous allez vous préparer à utiliser Graphics Diagnostics pour la première fois, puis vous allez capturer des frames à partir d’une application Direct3D et les examiner dans Graphics Analyzer.

## <a name="requirements"></a>Spécifications
 Pour utiliser Graphics Diagnostics dans Visual Studio, vous devez utiliser Visual Studio Enterprise, Visual Studio Professional ou Visual Studio Community.  D’autres éditions, y compris les Visual Studio Code, ne contiennent pas cette fonctionnalité.

 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]

### <a name="windows-10-prerequisites"></a>Prérequis pour Windows 10
 La fonctionnalité Windows facultative *Outils Graphics* fournit l’infrastructure de capture et de lecture nécessaire à Graphics Diagnostics sur Windows 10.

 Pour plus d’informations sur l’installation de la fonctionnalité Outils Graphics, consultez [Installer Outils Graphics pour Windows 10](#InstallGraphicsTools).

## <a name="install-graphics-tools-for-windows-10"></a><a name="InstallGraphicsTools"></a> Installer Outils Graphics pour Windows 10
 Dans Windows 10, l’infrastructure Graphics Diagnostics est fournie par une fonctionnalité facultative de Windows appelée *Outils Graphics*. Cette fonctionnalité est nécessaire pour capturer et lire les informations graphiques sur Windows 10, indépendamment du fait que l'application capturée cible ou non une version antérieure de Windows, ou indépendamment de la version de Direct3D utilisée. Vous pouvez choisir d'installer la fonctionnalité Outils Graphics à l'avance. Sinon, elle est installée à la demande la première fois que vous démarrez une session Graphics Diagnostics à partir de Visual Studio.

#### <a name="to-install-graphics-tools-for-windows-10"></a>Pour installer Outils Graphics pour Windows 10

1. Dans Rechercher, tapez **applications et fonctionnalités** , puis ouvrez les paramètres **applications & fonctionnalités** .

2. Sur le côté droit des paramètres **applications & fonctionnalités** , choisissez **fonctionnalités facultatives** (sous **applications & fonctionnalités**).

   Les paramètres **facultatifs des fonctionnalités** s’affichent.

3. Dans les paramètres **fonctionnalités facultatives** , choisissez **Ajouter une fonctionnalité**. Une liste de fonctionnalités facultatives que vous pouvez installer s'affiche.

4. Sélectionnez **Outils Graphics** dans la liste des fonctionnalités, puis choisissez **Installer**.

   La fonctionnalité Outils Graphics est également installée automatiquement quand vous installez le Kit de développement logiciel (SDK) Windows 10.

> [!TIP]
> La fonctionnalité facultative Outils Graphics de Windows 10 fournit des fonctionnalités légères de capture et de lecture (telles que le programme en ligne de commande de capture **dxcap.exe**) qui peuvent être utilisées dans les scénarios de prise en charge, de test et de diagnostic sur les ordinateurs où les outils de développement ne sont pas installés. Pour plus d’informations, consultez la rubrique [Outil en ligne de commande de capture](command-line-capture-tool.md).

## <a name="using-graphics-diagnostics-for-the-first-time"></a>Utilisation de Graphics Diagnostics pour la première fois
 Une fois que vous avez tout ce dont vous avez besoin, vous êtes prêt à utiliser Graphics Diagnostics. Suivez simplement cette procédure.

### <a name="1---create-a-direct3d-app"></a>1 - Créer une application Direct3D

Si vous avez déjà votre propre application Direct3D pour explorer Graphics Diagnostics avec, c’est génial ! Dans le cas contraire, utilisez l’une des options suivantes :

::: moniker range=">=vs-2019"
Téléchargez un exemple à partir de l' [exemple de jeu Direct3D](/samples/microsoft/windows-universal-samples/simple3dgamedx/).
::: moniker-end
::: moniker range="vs-2017"
- Les modèles de projet **application DirectX 11 (Windows universel)** ou **application DirectX 12 (Windows universel)** pour Windows 10.
- [Exemple d’UAP Direct3D 12](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) pour Windows 10.
::: moniker-end

Assurez-vous que vous pouvez générer et exécuter l’application avant de poursuivre. Choisissez **générer** générer la  >  **solution** pour vous assurer qu’il se génère sans erreur. Choisissez ensuite **Déboguer**  >  **exécuter sans débogage** (**CTRL + F5**) pour vous assurer qu’il s’exécute correctement. En fonction de l’ordinateur que vous testez avec l’outil, vous devrez peut-être ajuster la plateforme et la cible de débogage pour l’exemple. Par exemple, pour tester la plateforme x64 sur votre ordinateur hôte Visual Studio, choisissez **x64** comme plateforme de solution et **ordinateur local** comme cible de débogage. 

### <a name="2---start-a-graphics-diagnostics-session"></a>2 - Démarrer une session Graphics Diagnostics
 Maintenant, vous êtes prêt à démarrer votre première session Graphics Diagnostics. Dans Visual Studio, dans le menu principal, choisissez **Déboguer, graphiques, démarrer le débogage graphique**, ou appuyez simplement sur **Alt + F5**. Cela entraîne le démarrage de votre application dans Graphics Diagnostics et l’affichage des fenêtres de session de diagnostic dans Visual Studio.

> [!IMPORTANT]
> Si vous exécutez votre application sur Windows 10 et si vous n'avez pas encore installé la fonctionnalité facultative Outils Graphics, vous êtes invité à le faire maintenant. Vous devez l’installer avant de pouvoir utiliser Graphics Diagnostics sur Windows 10.

### <a name="3---capture-frames"></a>3 - Capturer des frames
 Vous êtes prêt à capturer des frames dès le démarrage de votre application.

#### <a name="to-capture-single-frames"></a>Pour capturer des frames uniques

- Dans Visual Studio, choisissez le bouton **Capturer le frame** à partir de la barre d’outils Graphics ou de la fenêtre de session de diagnostic. Ou, si votre application a le focus, appuyez simplement sur la touche **Impr. écran** de votre clavier.

#### <a name="to-capture-a-sequence-of-frames"></a>Pour capturer une séquence de frames

- Dans Visual Studio, dans la fenêtre de session de diagnostic, affectez à **Nombre de frames à capturer** le nombre de frames à capturer dans la séquence, puis capturez la séquence en utilisant l’une des méthodes ci-dessus pour capturer des frames uniques.

   Pour capturer à nouveau des frames uniques, affectez à **Nombre de frames à capturer** la valeur *1*.

  Une fois que vous avez fini de capturer les frames, quittez simplement l’application, ou choisissez le bouton **Arrêter** dans la barre d’outils Graphics ou la fenêtre de session de diagnostic.

### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4 - Examiner les frames capturés dans Graphics Analyzer
 À présent, vous êtes prêt à examiner les frames que vous venez de capturer. Pour démarrer l'analyse d'un frame, choisissez le numéro du frame que vous souhaitez examiner à partir de la fenêtre de session de diagnostic. Cela entraîne l’ouverture du frame dans **Graphics Analyzer**, où vous pouvez soit utiliser les outils Graphics Diagnostics pour examiner la façon dont votre application utilise Direct3D pour détecter les problèmes de rendu, soit utiliser l’outil **Analyse des frames** pour comprendre ses performances.

 Si vous avez sélectionné le mauvais frame dans la fenêtre de session de diagnostic, ou si vous souhaitez examiner un autre frame, vous pouvez en sélectionner un nouveau dans Graphics Analyzer. Sous l’onglet **Restituer la cible** de la fenêtre du journal de graphisme, sous l’image de la cible de rendu, développez la **Liste de frames**, puis choisissez un autre frame à examiner.

 Pour en savoir plus sur l’utilisation conjointe des outils Graphics Analyzer, consultez les [exemples](graphics-diagnostics-examples.md).

## <a name="see-also"></a>Voir aussi
- [Graphismes Direct3D 12](/windows/desktop/direct3d12/direct3d-12-graphics)