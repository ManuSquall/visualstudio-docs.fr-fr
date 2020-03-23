---
title: Configuration requise pour l’émulateur Visual Studio pour Android | Microsoft Docs
ms.custom: ''
ms.prod: visual-studio-dev15
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 35e766ad-269f-41e4-ba23-74a556c315f3
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f1462769a4ba9929a000bca998c1fe3708908798
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77272046"
---
# <a name="system-requirements-for-the-visual-studio-emulator-for-android"></a>Configuration système requise pour l'Émulateur Visual Studio pour Android

L’émulateur Visual Studio pour Android s’exécute en tant que machine virtuelle sur Hyper-V, la technologie de virtualisation pour Windows 8 et versions ultérieures. Pour exécuter l’émulateur, votre ordinateur doit satisfaire à la configuration requise pour exécuter Hyper-V, comme décrit dans cette rubrique.

Le programme d’installation tente de satisfaire à ces conditions préalables de manière silencieuse quand vous installez l’émulateur. Une fois qu’il a configuré correctement les composants requis, l’émulateur fonctionne simplement comme prévu. Dans le cas contraire, vous devrez activer ces composants requis manuellement. Si vous devez configurer manuellement les composants requis, les outils et les étapes sont identiques à ceux décrits [ici](/previous-versions/windows/apps/jj863509\(v=vs.105\)) pour l’émulateur Windows Phone.

> [!IMPORTANT]
> Le programme d’installation de l’émulateur vérifie les conditions préalables pour l’exécution de l’émulateur Visual Studio pour Android. Il affiche des avertissements si les composants requis ne sont pas présents, mais il ne les exige pas.

## <a name="quick-checklist"></a><a name="Checklist"></a>Liste de contrôle rapide

Voici une liste de vérification rapide des composants requis pour l’exécution de l’émulateur Visual Studio pour Android. Pour obtenir des informations détaillées, consultez les sections suivantes de cette rubrique.

Configuration système requise

- Prise en charge d’Hyper-V (voir la configuration requise pour Hyper-V ci-dessous)

- 6 Go de RAM ou plus.

- Version 64 bits de l’édition professionnelle de Windows 8, Windows 8.1, Windows 10 ou version ultérieure

- Processeur qui prend en charge SSSE3 ou version ultérieure.

Configuration requise pour le réseau

- DHCP

- Paramètres DNS et de passerelle configurés automatiquement

Configuration requise pour Hyper-V

- Dans le BIOS, les fonctionnalités suivantes doivent être prises en charge :

  - Assistance matérielle à la virtualisation

  - Traduction d’adresse de second niveau (SLAT)

  - Prévention de l’exécution des données (DEP) matérielle

- Dans Windows, Hyper-V doit être activé et en cours d’exécution.

- Vous devez être membre du groupe local Administrateurs Hyper-V.

## <a name="system-requirements"></a>Configuration système requise
 Votre ordinateur doit remplir les conditions suivantes :

- Prise en charge Hyper-V (consultez [Configuration requise pour Hyper-V](#hyper-v-requirements))

- 6 Go de RAM ou plus.

- Version 64 bits de Windows 8 Professionnel, Windows 8.1 Professionnel, Windows 10 Professionnel ou version ultérieure

Pour vérifier la configuration requise pour la RAM et Windows, dans le Panneau de configuration, choisissez Système et sécurité, puis Système.

![Vérifier la configuration système requise](../cross-platform/media/android_emu_system_requirements.png "Android_Emu_System_Requirements")

## <a name="network-requirements"></a>Configuration requise pour le réseau

Votre réseau doit remplir les conditions suivantes :

- DHCP

   L'émulateur nécessite le protocole DHCP, car il se configure lui-même comme périphérique distinct sur le réseau avec sa propre adresse IP.

- Paramètres DNS et de passerelle configurés automatiquement

   Vous ne pouvez pas configurer les paramètres DNS et de passerelle manuellement pour l’émulateur.

  Pour résoudre les problèmes de mise en réseau dans l’émulateur, consultez les rubriques suivantes :

- [Résolution des problèmes liés à l’émulateur Visual Studio pour Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)

## <a name="hyper-v-requirements"></a>Configuration requise pour Hyper-V

Configuration requise pour Hyper-V dans le BIOS

Le BIOS de votre ordinateur doit prendre en charge les spécifications suivantes et elles doivent être activées :

- Assistance matérielle à la virtualisation

- Traduction d’adresse de second niveau (SLAT)

- Prévention de l’exécution des données (DEP) matérielle

Configuration requise pour Hyper-V dans Windows

Quand les paramètres du BIOS et de votre ordinateur sont déjà configurés pour prendre en charge Hyper-V, le programme d’installation active et démarre Hyper-V. Dans le cas contraire, vous devrez peut-être activer manuellement ces composants requis.

|Condition requise|Comment vérifier et activer cette spécification|
|-----------------|----------------------------------------------|
|Hyper-V doit être installé|Suivez les mêmes instructions que celles utilisées pour [activer Hyper-V pour l’émulateur Windows Phone](/previous-versions/windows/apps/jj863509(v=vs.105)).<br /><br /> Vérifiez l’état du service **Gestion d’ordinateurs virtuels Hyper-V** dans le composant logiciel enfichable Services.|
|Hyper-V doit être en cours d’exécution.|Pour plus d’informations sur la gestion des services, consultez les rubriques suivantes :<br /><br /> -   [Démarrer, arrêter, faire une pause, reprendre ou redémarrer un service](https://technet.microsoft.com/library/cc736564\(v=WS.10\).aspx)<br />-   [Configurer comment un service est démarré](https://technet.microsoft.com/%20library/cc739213\(v=ws.10\))|

 Vous devez être membre du groupe local Administrateurs Hyper-V.

 Pour exécuter l’émulateur Visual Studio pour Android sans qu’une invite d’élévation de vos droits ne s’affiche de façon répétée, vous devez être membre du groupe local Administrateurs Hyper-V. Si vous êtes déjà un administrateur local sur l’ordinateur quand vous installez le Kit de développement logiciel, le programme d’installation du kit SDK vous ajoute au groupe Administrateurs Hyper-V. Dans le cas contraire, vous devrez activer cette spécification manuellement.

 Quand vous exécutez l’émulateur, si vous n’êtes pas encore membre du groupe Administrateurs Hyper-V, vous êtes invité à rejoindre le groupe (la boîte de dialogue fait référence à l’émulateur Windows Phone). Rejoindre le groupe nécessite des droits d’administrateur.

> [!IMPORTANT]
> Une fois que vous avez rejoint le groupe, déconnectez-vous ou redémarrez l’ordinateur pour que la modification prenne effet.

 ![Rejoindre le groupe de sécurité Hyper&#45;V Administrators](../cross-platform/media/android_emu_hyperv_admin.png "Android_Emu_HyperV_Admin")

 Pour vous ajouter à un groupe manuellement, ouvrez le composant logiciel enfichable Utilisateurs et groupes locaux.

## <a name="running-the-emulator-from-a-bootable-vhd-is-not-supported"></a>L’exécution de l’émulateur à partir d’un disque dur virtuel démarrable n’est pas prise en charge
 Si vous essayez d’exécuter une application sur l’émulateur Visual Studio pour Android pendant que vous exécutez Windows à partir d’un disque dur virtuel démarrable, le démarrage de l’émulateur prend généralement plusieurs minutes ou échoue. Quand le démarrage de l’émulateur échoue, le message suivant s’affiche : Échec du déploiement de l’application. Réessayez.

 Cette configuration n’est pas prise en charge. Pour plus d’informations sur les problèmes connexes, consultez [Résoudre les problèmes de l’émulateur Visual Studio pour Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).

## <a name="hyper-v-requires-uncompressed-and-unencrypted-files"></a>Hyper-V nécessite des fichiers non compressés et non chiffrés
 Sur un disque dur configuré avec le système de fichiers NTFS, les fichiers de disque dur virtuel utilisés par Hyper-V doivent être non compressés et non chiffrés. Assurez-vous que les répertoires suivants ne sont pas compressés ou chiffrés :

- %localappdata%\Microsoft\XDE

- C:\Program Files (x86)\Microsoft Emulator Manager

- C:\Program Files (x86)\Microsoft Visual Studio Emulator for Android

- %localappdata%\Microsoft\VisualStudioEmulator

Sur le système de fichiers ReFS, les fichiers de disque dur virtuel ne doivent pas avoir le bit d’intégrité défini.

## <a name="hardware-graphics-forwarding-opengl-es-support-requirements"></a>Configuration requise relative au transfert graphique matériel (prise en charge d’OpenGL ES)

Pour que l’émulateur émule les appels au GPU, tels que ceux utilisés par OpenGL ES, votre ordinateur doit avoir un GPU compatible DirectX avec les pilotes DirectX appropriés installés.

## <a name="see-also"></a>Voir aussi

- [Résoudre les problèmes de l’émulateur Visual Studio pour Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
