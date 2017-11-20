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
ms.openlocfilehash: 27cff46f5a68ef28f247aa159a2b8be5db56b0fe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
Si vous avez installé le déploiement Web à l’aide de Web Platform Installer, vous pouvez déployer l’application directement à partir de Visual Studio.

1. Démarrez Visual Studio avec des privilèges d’administrateur et rouvrez le projet.

    Des privilèges d’administrateur sont requis pour déployer votre application à l’aide de Web Deploy.

2. Dans l’ **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de projet et sélectionnez **Publier**.

3. Pour **sélectionner une cible de publication**, sélectionnez **IIS, FTP, etc.** et cliquez sur **publier**.

    ![RemoteDBG_Publish_IISl](../media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

4. Entrez les paramètres de configuration de correction pour l’installation d’IIS.

    ![RemoteDBG_Publish_WebDeployl](../media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Si un nom d’hôte ne résout pas lorsque vous essayez de validation en suivant les étapes le **Server** texte zone, essayez de l’adresse IP. Inclure `http://` en tant que préfixe dans le **Server** champ.  Assurez-vous que vous utilisez le port 80 dans le **Server** texte zone et vous assurer que le port 80 est ouvert dans le pare-feu.

6. Cliquez sur **suivant**, choisissez un **déboguer** configuration, choisissez **supprimer les fichiers supplémentaires à la destination** sous le **fichier publier** Options.

    > [!NOTE]
    > Si vous choisissez une configuration Release, vous désactivez le débogage dans le fichier web.config lorsque vous publiez.

5. Cliquez sur **Prev**, puis choisissez **Validate**. Si le programme d’installation de connexion valide, essayez de publier.

6. Cliquez sur **publier** pour publier l’application.

    L’onglet sortie vous indique si la publication a réussi, et l’application ouvre votre navigateur.

    Si vous obtenez une erreur mentionnant Web Deploy, vérifiez à nouveau les étapes d’installation Web Deploy et assurez-vous que les ports appropriés sont ouverts (Web Deploy requiert également le port 8172 ouvert sur le serveur).

    Si l’application se déploie correctement, mais elle ne s’exécute pas correctement, il peut y avoir un problème avec votre configuration IIS, l’installation d’ASP.NET ou la configuration de votre site Web. Sur le serveur Windows, ouvrez le site Web d’IIS pour les messages d’erreur plus spécifiques et puis revérifiez les étapes précédentes.