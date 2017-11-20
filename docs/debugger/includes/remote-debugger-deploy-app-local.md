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
ms.openlocfilehash: a55b2a12c9a45c5a3952e3e6f4e1627bec8ba520
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
1. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **publier** (pour Web Forms, **publier l’application Web**).

2. Dans le **publier** boîte de dialogue, sélectionnez **dossier**, cliquez sur **Parcourir**et créer un nouveau dossier, **C:\Publish**.

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    Pour une application Web Forms, choisissez **personnalisé** dans la boîte de dialogue Publier, entrez un nom de profil, puis choisissez **OK**.

3. Cliquez sur **Publier**.

    Visual Studio publie le projet dans le dossier. Progression s’affiche dans la fenêtre Sortie.

4. Dans le **publier** boîte de dialogue, cliquez sur le **paramètres** lier, puis sélectionnez le **paramètres** onglet.

5. La configuration de la valeur **déboguer**, sélectionnez **supprimer tous les fichiers existants avant de publier**, puis cliquez sur **enregistrer**.

    > [!NOTE]
    > Si vous utilisez une version Release, vous désactivez le débogage dans le fichier web.config lorsque vous publiez.

6. Cliquez sur **Publier**.

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")
    
    L’application publie un **déboguer** configuration du projet dans le dossier local.

5. Copiez le répertoire du projet ASP.NET à partir de l’ordinateur Visual Studio dans le répertoire local est configuré pour l’application ASP.NET (dans cet exemple, **C:\Publish**) sur l’ordinateur Windows Server. Dans ce didacticiel, nous supposons que vous copiez manuellement, mais vous pouvez utiliser d’autres outils tels que PowerShell, Xcopy ou Robocopy.

    > [!CAUTION]
    >  Si vous devez apporter des modifications à du code ou la régénération, vous devez republier et répétez cette étape. Le fichier exécutable que vous avez copié sur l’ordinateur distant doit correspondre exactement à la source et aux symboles locaux.

6. Sur le serveur Windows, vérifiez que vous pouvez exécuter l’application correctement en ouvrant l’application dans votre navigateur.

    Si l’application ne s’exécute pas correctement, il peut y avoir une incompatibilité entre la version d’ASP.NET installés sur votre serveur et sur votre ordinateur Visual Studio, ou vous pouvez avoir un problème avec votre configuration d’IIS ou le site Web. Revérifier les étapes précédentes.