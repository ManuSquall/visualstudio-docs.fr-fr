---
title: Déboguer des applications UWP sur des ordinateurs distants | Microsoft Docs
description: Découvrez comment utiliser Visual Studio pour exécuter, déboguer, Profiler et tester une application plateforme Windows universelle (UWP) à distance sur un autre ordinateur ou appareil.
ms.custom: SEO-VS-2020
ms.date: 10/05/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: a28769237f0c1b0078e9c9c117695e68e5b521ac
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204954"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>Déboguer des applications UWP sur des ordinateurs distants à partir de Visual Studio

Vous pouvez utiliser Visual Studio pour exécuter, déboguer, Profiler et tester une application plateforme Windows universelle (UWP) sur un autre ordinateur ou appareil. L’exécution de l’application UWP sur un ordinateur distant est particulièrement utile lorsque l’ordinateur Visual Studio ne prend pas en charge les fonctionnalités spécifiques au UWP, telles que la saisie tactile, la géolocalisation ou l’orientation physique.

## <a name="prerequisites"></a><a name="BKMK_Prerequisites"></a> Conditions préalables

Pour déboguer une application UWP sur un appareil distant à partir de Visual Studio :

- Le projet Visual Studio doit être configuré pour le débogage distant.
- L’ordinateur distant et l’ordinateur Visual Studio doivent être connectés sur un réseau ou directement via un câble USB ou Ethernet. Le débogage sur Internet n'est pas pris en charge.
- Vous devez [activer le mode développeur](/windows/uwp/get-started/enable-your-device-for-development) sur l’ordinateur Visual Studio et sur l’ordinateur distant.
- Les ordinateurs distants doivent exécuter le Outils de contrôle à distance de Visual Studio.
  - Certaines versions de Windows 10 démarrent et exécutent automatiquement les outils de contrôle à distance. Dans le cas contraire, [Installez et exécutez le outils de contrôle à distance de Visual Studio](#BKMK_download).
  - Les appareils Windows Mobile 10 ne nécessitent pas ou ne prennent pas en charge les outils de contrôle à distance.

## <a name="configure-a-visual-studio-project-for-remote-debugging"></a><a name="BKMK_ConnectVS"></a> Configurer un projet Visual Studio pour le débogage distant
<a name="BKMK_DirectConnect"></a> Vous utilisez les **Propriétés** du projet pour spécifier l’appareil distant auquel se connecter. Les paramètres varient en fonction du langage de programmation.

> [!CAUTION]
> Par défaut, la page de propriétés définit le **type d’authentification** **universel (protocole non chiffré)** pour les connexions à distance Windows 10. Vous devrez peut-être définir **aucune authentification** pour vous connecter au débogueur distant. Le **protocole universel (protocole non chiffré)** et **aucun protocole d’authentification** n’ont aucune sécurité réseau. les données transmises entre le développement et les ordinateurs distants sont donc vulnérables. Choisissez ces types d’authentification uniquement pour les réseaux approuvés dont vous êtes sûr qu’ils ne sont pas exposés à un trafic malveillant ou hostile.
>
>Si vous choisissez l' **authentification Windows** pour le **type d’authentification**, vous devrez vous connecter à l’ordinateur distant lors du débogage. Le débogueur distant doit également s’exécuter en mode **d’authentification Windows** , avec le même compte d’utilisateur que sur l’ordinateur Visual Studio.

### <a name="configure-a-c-or-visual-basic-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Configurer un projet C# ou Visual Basic pour le débogage distant

1. Sélectionnez le projet C# ou Visual Basic dans Visual Studio **Explorateur de solutions** puis sélectionnez l’icône **Propriétés** , appuyez sur **ALT** + **entrée**, ou cliquez avec le bouton droit et choisissez **Propriétés**.

1. Sélectionnez l’onglet **Débogage**.

1. Sous **périphérique cible**, sélectionnez **ordinateur distant** pour un ordinateur distant ou un **appareil** pour un appareil Windows Mobile 10 connecté en direct.

1. Pour une machine distante, entrez le nom du réseau ou l’adresse IP dans le champ **ordinateur distant** , ou sélectionnez **Rechercher** pour Rechercher l’appareil dans la [boîte de dialogue connexions à distance](#remote-connections).

    ![Propriétés du projet managé pour le débogage distant](../debugger/media/vsrun_managed_projprop_remote.png "Propriétés du projet de débogage managé")

### <a name="configure-a-c-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Configurer un projet C++ pour le débogage distant

1. Sélectionnez le projet C++ dans Visual Studio **Explorateur de solutions** puis sélectionnez l’icône **Propriétés** , appuyez sur **ALT** + **entrée**, ou cliquez avec le bouton droit et choisissez **Propriétés**.

1. Sélectionnez l’onglet **débogage** .

3. Sous **débogueur à lancer**, sélectionnez **machine distante** pour un ordinateur distant ou un **appareil** pour un appareil Windows Mobile 10 à connexion directe.

1. Pour une machine distante, entrez ou sélectionnez le nom du réseau ou l’adresse IP dans le champ nom de l' **ordinateur** , ou cliquez sur le menu déroulant, puis sélectionnez **Rechercher** pour Rechercher l’appareil dans la [boîte de dialogue connexions à distance](#remote-connections).

    ![Propriétés du projet C++ pour le débogage distant](../debugger/media/vsrun_cpp_projprop_remote.png "Propriétés du projet de débogage C++")

### <a name="use-the-remote-connections-dialog-box"></a><a name="remote-connections"></a> Utiliser la boîte de dialogue connexions à distance

Dans la boîte de dialogue **connexions à distance** , vous pouvez rechercher un nom d’ordinateur distant ou une adresse IP spécifique, ou détecter automatiquement les connexions en sélectionnant l’icône d’actualisation des flèches arrondies. La boîte de dialogue recherche uniquement les périphériques sur le sous-réseau local qui exécutent actuellement le débogueur distant. Tous les appareils ne peuvent pas être détectés dans la boîte de dialogue **connexions à distance** .

 ![Boîte de dialogue Connexion à distance](../debugger/media/vsrun_selectremotedebuggerdlg.png "Boîte de dialogue connexions à distance")

>[!TIP]
>Si vous ne pouvez pas vous connecter à un appareil distant par son nom, essayez d’utiliser son adresse IP. Pour déterminer l’adresse IP, sur le périphérique distant, entrez **ipconfig** dans une fenêtre de commande. L’adresse IP apparaît en tant qu' **adresse IPv4**.

## <a name="download-and-install-the-remote-tools-for-visual-studio"></a><a name="BKMK_download"></a> Télécharger et installer les outils de contrôle à distance de Visual Studio

Pour que Visual Studio débogue des applications sur un ordinateur distant, l’ordinateur distant doit exécuter le Outils de contrôle à distance de Visual Studio.

- Les appareils Windows Mobile 10 ne nécessitent pas ou ne prennent pas en charge les outils de contrôle à distance.
- Les PC Windows 10 qui exécutent la mise à jour du créateur (version 1703) et versions ultérieures, les appareils Windows 10 Xbox, IoT et HoloLens installent automatiquement les outils de contrôle à distance lorsque vous déployez l’application.
- Sur les PC Windows 10 de mise à jour du pré-créateur, vous devez télécharger, installer et exécuter manuellement les outils de contrôle à distance sur l’ordinateur distant avant de commencer le débogage.

**Pour télécharger et installer les outils de contrôle à distance :**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="configure-the-remote-tools"></a><a name="BKMK_setup"></a> Configurer les outils de contrôle à distance

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

## <a name="debug-uwp-apps-remotely"></a><a name="BKMK_RunRemoteDebug"></a> Déboguer des applications UWP à distance

Le débogage distant fonctionne de la même façon que le débogage local.

1. Sur les versions de mise à jour du pré-créateur de Windows 10, assurez-vous que le Remote Debugging Monitor (*msvsmon.exe*) est en cours d’exécution sur l’appareil distant.

1. Sur l’ordinateur Visual Studio, assurez-vous que la cible de débogage appropriée (machine ou **périphérique****distant** ) s’affiche en regard de la flèche verte dans la barre d’outils.

1. Démarrez le débogage en sélectionnant **Déboguer**  >  **Démarrer le débogage**, en appuyant sur **F5** ou en sélectionnant la flèche verte dans la barre d’outils.

   Le projet est recompilé, puis déployé et démarré sur le périphérique distant. Le débogueur interrompt l’exécution aux points d’arrêt et vous pouvez effectuer un pas à pas détaillé, principal et sortant du code.

1. Si nécessaire, sélectionnez **Déboguer**  >  **arrêter le débogage** ou appuyez sur **MAJ** + **F5** pour arrêter le débogage et fermer l’application distante.

## <a name="see-also"></a>Voir aussi
- [Options avancées de déploiement distant](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Test d’applications UWP avec Visual Studio](../test/unit-test-your-code.md)
- [Déployer des applications UWP dans Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
