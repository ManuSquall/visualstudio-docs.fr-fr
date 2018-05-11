---
translation.priority.ht:
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
ms.openlocfilehash: c22ba73b464f91bf3036541304cdf94e8660970d
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
1. Si vous prévoyez de déployer vos applications avec Web Deploy dans Visual Studio, installez la dernière version de Web Deploy sur le serveur.

    Pour installer Web Deploy, utilisez le [Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Pour rechercher le lien Web Platform Installer à partir de IIS, sélectionnez **IIS** dans le volet gauche du Gestionnaire de serveur. Cliquez sur le serveur et sélectionnez **Gestionnaire des Services Internet (IIS)**.)

    Web Platform Installer, vous trouverez dans Web Deploy dans l’onglet Applications. Vous pouvez également obtenir un programme d’installation directement à partir de la [Microsoft Download Center](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc). 

2. Vérifiez que Web Deploy s’exécute correctement en ouvrant **le panneau de configuration > système et sécurité > Outils d’administration > Services** et assurez-vous que **Service de l’Agent de déploiement Web** est en cours d’exécution (la nom du service est différent dans les versions antérieures).

    Si le service agent n’est pas en cours d’exécution, démarrez-le. Si elle ne figure pas du tout, accédez à **le panneau de configuration > Programmes > désinstaller un programme**, recherchez **Microsoft Web Deploy <version>** . Choisissez de **modification** l’installation et vérifiez que vous choisissez **sera installé sur le disque dur local** pour les composants Web Deploy. Effectuez les étapes d’installation de modification.