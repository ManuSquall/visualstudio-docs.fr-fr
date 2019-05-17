---
title: Débloquer le téléchargement des outils à distance
ms.date: 07/19/2018
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a243033bf5831952d83fdf688302651e02b76b7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62903020"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>Procédure : Débloquer le téléchargement des outils à distance sur Windows Server

Les paramètres de sécurité par défaut dans Internet Explorer sur Windows Server peuvent rendre fastidieuse télécharger les composants, tels que les outils à distance.

* Configuration de sécurité renforcée est activée sur Internet Explorer, ce qui vous empêche d’ouvrir des sites Web et l’accès aux ressources web, sauf si le domaine contenant la ressource est explicitement autorisé (autrement dit, approuvé). Bien que vous pouvez désactiver ce paramètre, nous déconseillons il, car il peut présenter un risque de sécurité.

* Sur Windows Server 2016, un paramètre par défaut dans **Options Internet** > **sécurité** > **Internet**  >   **Personnaliser le niveau** > **télécharge** également désactive les téléchargements de fichiers. Si vous choisissez de télécharger les outils à distance directement sur Windows Server, vous devez activer le téléchargement du fichier.

Pour télécharger les outils de Windows Server, nous vous recommandons une des opérations suivantes :

* Téléchargez les outils à distance sur un autre ordinateur, telles que l’exécution de Visual Studio et puis copiez le *.exe* fichier vers Windows Server.

* Exécuter le débogueur distant [à partir d’un partage de fichiers](../debugger/remote-debugging.md#fileshare_msvsmon) sur votre ordinateur Visual Studio.

* Téléchargez les outils à distance directement sur Windows Server et acceptez les invites pour ajouter des sites de confiance. Sites Web modernes incluent souvent de nombreuses ressources de tiers, donc cela peut entraîner de nombreuses invites. En outre, des liens redirigés peuvent avoir à être ajoutés manuellement. Vous pouvez choisir d’ajouter les sites de confiance avant de commencer le téléchargement. Accédez à **Options Internet > sécurité > Sites de confiance > Sites** et ajoutez les sites suivants.

  * visualstudio.microsoft.com
  * download.visualstudio.microsoft.com
  * à propos : vide

  Pour les versions antérieures du débogueur sur my.visualstudio.com, ajoutez ces sites supplémentaires pour vous assurer que la connexion est réussie :

  * microsoft.com
  * go.microsoft.com
  * download.microsoft.com
  * my.visualstudio.com
  * login.microsoftonline.com
  * login.live.com
  * secure.aadcdn.microsoftonline-p.com
  * msft.sts.microsoft.com
  * auth.gfx.ms
  * app.vssps.visualstudio.com
  * vlscppe.microsoft.com
  * query.prod.cms.rt.microsoft.com

    Si vous choisissez d’ajouter ces domaines lors du téléchargement des outils à distance, puis choisissez **ajouter** lorsque vous y êtes invité.

    ![Boîte de dialogue de contenu bloqué](../debugger/media/remotedbg-blocked-content.png)

    Lorsque vous téléchargez le logiciel, vous obtenez certaines demandes supplémentaires pour accorder des autorisations requises pour charger des différents scripts de site web et des ressources. Sur my.visualstudio.com, nous vous recommandons d’ajouter les domaines supplémentaires pour vous assurer que la connexion est réussie.