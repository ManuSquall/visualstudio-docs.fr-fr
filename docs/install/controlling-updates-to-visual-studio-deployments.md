---
title: "Contrôler les mises à jour applicables aux déploiements de Visual Studio | Microsoft Docs"
description: "{{ESPACE RÉSERVÉ}}"
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 2e68d084c88c398d1576f53a79a156c111651895
ms.contentlocale: fr-fr
ms.lasthandoff: 05/09/2017

---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau

Les administrateurs d’entreprise créent souvent une disposition qu’ils hébergent sur un partage de fichiers réseau en vue d’un déploiement sur les utilisateurs finaux.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Contrôle de l’emplacement où Visual Studio recherche des mises à jour
Par défaut, Visual Studio continue de rechercher en ligne des mises à jour même si l’installation a été déployée à partir d’un partage réseau. Si une mise à jour est disponible, l’utilisateur est en mesure de l’installer ; tout contenu mis à jour qui est introuvable dans la disposition en mode hors connexion est téléchargé à partir du web.

Si vous souhaitez un contrôle direct sur l’emplacement où Visual Studio recherche des mises à jour, ainsi que la version vers laquelle vos utilisateurs sont mis à jour, vous pouvez modifier cet emplacement en suivant ces étapes :

 1. Créez une disposition en mode hors connexion :
    ```
    vs_enterprise.exe --layout C:\vs2017offline --lang en-US
    ```
 2. Copiez-la dans le partage de fichiers dans lequel vous souhaitez l’héberger :
    ```
    xcopy /e C:\vs2017offline \\server\share\VS2017
    ```
 3. Modifiez le fichier response.json dans la disposition et modifiez la valeur `channelUri` pour qu’elle pointe vers une copie de channelManifest.json que contrôle l’administrateur. <b>Remarque :</b> Veillez à placer dans une séquence d’échappement les barres obliques inverses dans la valeur, comme suit :
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 4. Les utilisateurs finaux peuvent maintenant exécuter le programme d’installation à partir de ce partage pour installer Visual Studio.
    ```
    \\server\share\VS2017\vs_enterprise.exe
    ```
 5. Quand un administrateur d’entreprise détermine que le moment est venu pour les utilisateurs d’effectuer une mise à jour vers une version plus récente de Visual Studio, il peut [mettre à jour l’emplacement de la disposition](update-a-network-installation-of-visual-studio.md) pour intégrer les fichiers mis à jour avec une commande similaire à celle-ci :
    ```
    vs_enterprise.exe --layout \\server\share\VS2017 --lang en-US
    ```
 6. Vérifiez que le fichier response.json de la disposition mise à jour contient toujours vos personnalisations, en particulier la modification de channelUri :
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 7. Les installations existantes de Visual Studio à partir de cette disposition rechercheront les mises à jour sur `\\server\share\VS2017\ChannelManifest.json`. Si ce fichier channelManifest.json est plus récent que celui que l’utilisateur a installé, Visual Studio informe l’utilisateur qu’une mise à jour est disponible.
 8. Les nouvelles installations installeront automatiquement la version mise à jour de Visual Studio directement à partir de la disposition.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Contrôle des notifications dans l’IDE de Visual Studio
Comme décrit ci-dessus, Visual Studio vérifie l’emplacement à partir duquel il a été installé (par exemple, le partage réseau ou Internet), pour voir si des mises à jour sont disponibles. Quand une mise à jour est disponible, Visual Studio avertit par défaut l’utilisateur avec un indicateur de notification dans le coin supérieur droit de la fenêtre : ![Indicateur de notification des mises à jour](~/docs/install/media/notification-flag.png)

Si vous ne voulez pas que les utilisateurs finaux soient informés des mises à jour (par exemple, vous transmettez des mises à jour via un mécanisme de distribution de logiciels central), vous pouvez désactiver ces notifications.

Comme Visual Studio 2017 [stocke les entrées de Registre dans un Registre privé](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), vous ne pouvez pas modifier directement le Registre de façon normale. Toutefois, Visual Studio inclut une commande `vsregedit.exe` que vous pouvez utiliser pour modifier les paramètres de Visual Studio. Vous pouvez désactiver les notifications avec la commande suivante :

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2 dword 0
```

Remplacez le répertoire dans la commande ci-dessus pour qu’il corresponde à l’instance installée à modifier. 

> [!TIP]
> Utilisez [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) pour rechercher une instance spécifique de Visual Studio sur une station de travail cliente. 

## <a name="see-also"></a>Voir aussi
* [Installer Visual Studio](install-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Outils de gestion des instances de Visual Studio](tools-for-managing-visual-studio-instances.md)

