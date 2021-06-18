---
title: Mettre à jour une installation réseau
description: Découvrez comment mettre à jour une installation réseau de Visual Studio à l’aide de la commande --layout
ms.date: 05/26/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b833551d00f4bd8fb158c848d3bf5b48173e563b
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306655"
---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Mettre à jour une installation réseau de Visual Studio

Il est possible de mettre à jour une disposition d’installation réseau de Visual Studio avec les dernières mises à jour de produit, afin de pouvoir l’utiliser comme point d’installation de la dernière mise à jour de Visual Studio, et pour gérer aussi les installations déjà déployées sur les stations de travail clientes.

## <a name="how-to-update-a-network-layout"></a>Comment mettre à jour une disposition réseau

> [!IMPORTANT]
> Ces instructions supposent que vous avez déjà créé une disposition d’installation réseau et pris des décisions sur la façon dont le client est censé obtenir les mises à jour. Pour plus d’informations sur la procédure à suivre, consultez la page [créer une installation réseau de Visual Studio](create-a-network-installation-of-visual-studio.md) et [contrôler les mises à jour des déploiements Visual Studio](../install/controlling-updates-to-visual-studio-deployments.md) .

Pour actualiser votre partage d’installation réseau afin qu’il inclue les dernières mises à jour, exécutez le programme d’amorçage à l’aide du `--layout` paramètre pour télécharger les packages mis à jour.

Si vous avez sélectionné une disposition partielle lorsque vous avez [créé la disposition du réseau](create-a-network-installation-of-visual-studio.md), ces paramètres sont enregistrés. Toutes les commandes de disposition futures utilisent les options précédentes ainsi que toutes les nouvelles options que vous indiquez.

Si vous hébergez une disposition sur un partage de fichiers, vous devez mettre à jour une copie privée de la disposition (par exemple, c:\VSLayout), puis, une fois que tout le contenu mis à jour est téléchargé, copiez-le dans votre partage de fichiers (par exemple, \\ server\products\VS). Si vous ne le faites pas, il est très probable que les utilisateurs exécutant le programme d’installation pendant que vous mettez à jour la disposition ne soient pas en mesure de récupérer tout le contenu de la disposition, puisque celui-ci n’est pas encore totalement à jour.

Intéressons-nous de plus près à quelques exemples de création et de mise à jour d’une disposition :

* Tout d’abord, voyons un exemple montrant comment créer une disposition avec une charge de travail pour l’anglais uniquement :

  ```shell
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
  ```

* Voici comment mettre à jour cette même disposition vers une version plus récente. Vous n’êtes pas obligé de spécifier les paramètres de ligne de commande supplémentaires. Les paramètres précédents étaient enregistrés et ils vont être utilisés par toutes les commandes de disposition suivantes dans ce dossier de disposition.

  ```shell
  vs_enterprise.exe --layout c:\VSLayout
  ```

* Voici comment mettre à jour votre disposition avec une version plus récente en mode sans assistance. L’opération de disposition exécute le processus d’installation dans une nouvelle fenêtre de console. La fenêtre reste ouverte pour que les utilisateurs puissent voir le résultat final, ainsi qu’un récapitulatif des erreurs qui se sont produites. Si vous effectuez une opération de disposition en mode sans assistance (par exemple, si vous avez un script qui est exécuté régulièrement pour mettre à jour votre disposition vers la version la plus récente), utilisez le paramètre `--passive` pour que le processus ferme automatiquement la fenêtre.

  ```shell
  vs_enterprise.exe --layout c:\VSLayout --passive
  ```

* Voici comment ajouter une charge de travail supplémentaire et une langue localisée.  (Cette commande ajoute la charge de travail *développement Azure* .)  Désormais, Managed Desktop et Azure sont inclus dans cette disposition.  Les ressources de langue pour l’anglais et l’allemand sont également englobées pour toutes ces charges de travail.  De plus, la disposition est mise à jour avec la dernière version disponible.

  ```shell
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
  ```

    > [!IMPORTANT]
    > Une opération de mise à jour ne télécharge pas ou n’installe pas de composants facultatifs supplémentaires, que ce soit sur la disposition ou sur le client. Si vous devez ajouter ou modifier des composants facultatifs, commencez par supprimer les anciens composants facultatifs du `Layout.JSON` [fichier réponse](automated-installation-with-response-file.md) et incluez les nouveaux composants dont vous avez besoin dans la section « ajouter » de `Layout.JSON` . Ensuite, lorsque vous exécutez la commande de mise à jour sur la disposition, les composants nouvellement ajoutés sont téléchargés dans la disposition. 
    >
    > Pour installer ces nouveaux composants sur l’ordinateur client, assurez-vous d’effectuer les trois étapes suivantes. Tout d’abord, vérifiez que la disposition contient les nouveaux composants, comme décrit ci-dessus. Ensuite, mettez à jour votre client vers les derniers bits dans la disposition.  Enfin, sur le client, exécutez une opération de modification qui installe les nouveaux composants (ajoutés à la disposition) sur l’ordinateur client.

* Et pour finir, voici comment ajouter une charge de travail et une langue localisée supplémentaires sans mettre à jour la version. (Cette commande ajoute la charge de travail *de développement Web et ASP.net* .)  Les charges de travail de développement Web, Azure et & ASP.NET sont désormais incluses dans cette disposition. Les ressources de langue pour l’anglais, l’allemand et le français sont également englobées pour toutes ces charges de travail.  Toutefois, la disposition n’a été pas mise à jour vers la toute dernière version disponible lors de l’exécution de cette commande. Elle reste à la version existante.

  ```shell
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
  ```

## <a name="deploy-an-update-to-client-machines"></a>Déployer une mise à jour sur les ordinateurs clients

Selon la configuration de votre environnement réseau, une mise à jour peut être déployée par un administrateur d’entreprise ou lancée à partir d’un ordinateur client.

* Les utilisateurs peuvent mettre à jour une instance de Visual Studio qui a été installée à partir d’un dossier d’installation hors connexion :
  * Exécutez le programme d’installation de Visual Studio.
  * Cliquez ensuite sur **Mettre à jour**.

::: moniker range="vs-2017"

* Les administrateurs peuvent mettre à jour les déploiements de clients de Visual Studio sans aucune intervention utilisateur avec deux commandes distinctes :
  * Mettez tout d’abord à jour Visual Studio Installer : <br>```vs_enterprise.exe --quiet --update```
  * Mettez ensuite à jour l’application Visual Studio proprement dite : <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

::: moniker-end

::: moniker range="vs-2019"

* Les administrateurs peuvent mettre à jour les déploiements de clients de Visual Studio sans aucune intervention utilisateur avec deux commandes distinctes :
  * Mettez tout d’abord à jour Visual Studio Installer : <br>```vs_enterprise.exe --quiet --update```
  * Mettez ensuite à jour l’application Visual Studio proprement dite : <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart```

::: moniker-end

::: moniker range=">=vs-2022"

* Les administrateurs peuvent mettre à jour les déploiements de clients de Visual Studio sans aucune intervention utilisateur avec deux commandes distinctes :
  * Mettez tout d’abord à jour Visual Studio Installer : <br>```vs_enterprise.exe --quiet --update```
  * Mettez ensuite à jour l’application Visual Studio proprement dite : <br>```vs_enterprise.exe update --installPath "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" --quiet --wait --norestart```

::: moniker-end

> [!NOTE]
> Utilisez la [commande vswhere.exe](tools-for-managing-visual-studio-instances.md) pour identifier le chemin d’installation d’une instance existante de Visual Studio sur un ordinateur client.
>
> [!TIP]
> Pour plus d’informations sur le contrôle du moment de la présentation des notifications de mise à jour aux utilisateurs, consultez [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](controlling-updates-to-visual-studio-deployments.md).

## <a name="verify-a-layout"></a>Vérifier une disposition

Utilisez l’option `--verify` pour effectuer la vérification dans le cache hors connexion fourni. Elle contrôle si des fichiers de package sont manquants ou non valides. À la fin de la vérification, la liste des fichiers manquants et non valides est imprimée.

```shell
vs_enterprise.exe --layout <layoutDir> --verify
```

Le fichier vs_enterprise.exe peut être appelé à l’intérieur du répertoire layoutDir.

> [!NOTE]
> Certains fichiers de métadonnées importantes, qui sont nécessaires à l’option `--verify`, doivent se trouver dans le cache hors connexion de la disposition. Si ces fichiers de métadonnées sont manquants, "--verify" ne peut pas s’exécuter et le programme d’installation signale une erreur. Si vous rencontrez cette erreur, recréez une nouvelle disposition en mode hors connexion dans un dossier différent (ou dans le même dossier de cache hors connexion). Pour cela, exécutez la même commande de disposition que celle que vous avez utilisée pour créer la disposition hors connexion initiale. Par exemple : `vs_enterprise.exe --layout <layoutDir>`.

Comme Microsoft fournit régulièrement des mises à jour de Visual Studio, la version de la nouvelle disposition que vous créez peut donc être différente de celle de la disposition initiale.

> [!NOTE]
> La vérification fonctionne seulement pour la dernière version d’une version mineure spécifique de Visual Studio. Dès qu’une nouvelle version est publiée, la vérification ne fonctionne plus pour les versions du niveau de correctif antérieures de la même version mineure.

## <a name="fix-a-layout"></a>Corriger une disposition

Utilisez `--fix` pour effectuer la même vérification que `--verify` et pour tenter également de résoudre les problèmes identifiés. Le processus `--fix` nécessite une connexion Internet, ainsi vous devez vous assurer que votre ordinateur est connecté à Internet avant d’appeler `--fix`.

```shell
vs_enterprise.exe --layout <layoutDir> --fix
```

Le fichier vs_enterprise.exe peut être appelé à l’intérieur du répertoire layoutDir.

## <a name="remove-older-versions-from-a-layout"></a>Supprimer les anciennes versions d’une mise en page

Suite aux mises à jour de disposition que vous avez effectuées vers un cache hors connexion, le dossier du cache de disposition peut contenir quelques packages obsolètes qui ne sont plus utiles à la dernière installation en date de Visual Studio. Vous pouvez utiliser l’option `--clean` pour supprimer les packages obsolètes à partir d’un dossier de cache hors connexion.

Pour ce faire, vous avez besoin du chemin de fichier du ou des manifestes de catalogue qui contiennent les packages obsolètes. Vous pouvez trouver les manifestes de catalogue dans un dossier Archive situé dans le cache de disposition en mode hors connexion. Ils sont enregistrés à cet endroit lorsque vous mettez à jour une disposition. Dans le dossier Archive, il existe un ou plusieurs dossiers nommés GUID qui contiennent chacun un manifeste de catalogue obsolète. Le nombre de dossiers GUID doit être le même que le nombre de mises à jour apportées à votre cache hors connexion.

Quelques fichiers sont enregistrés à l’intérieur de chaque dossier GUID. Les deux fichiers les plus intéressants sont « catalog.json » et « version.txt ». Le fichier catalog.json est le manifeste de catalogue obsolète que vous devez passer à l’option `--clean`. L’autre fichier, version.txt, contient la version de ce manifeste de catalogue obsolète. En fonction du numéro de version, vous pouvez décider de supprimer ou non les packages obsolètes à partir de ce manifeste de catalogue. Vous pouvez en faire de même lorsque vous parcourez les autres dossiers GUID. Après avoir décidé du ou des catalogues à nettoyer, exécutez la commande `--clean` en spécifiant les chemins de fichier de ces catalogues.

Voici quelques exemples montrant comment utiliser l’option--clean :

```shell
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> <file-path-of-catalog2> …
```

```shell
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> --clean <file-path-of-catalog2> …
```

Vous pouvez aussi appeler le fichier vs_enterprise.exe à l’intérieur du répertoire &lt;layoutDir&gt;. Voici un exemple :

```shell
c:\VSLayout\vs_enterprise.exe --layout c:\VSLayout --clean c:\VSLayout\Archive\1cd70189-fc55-4583-8ad8-a2711e928325\Catalog.json --clean c:\VS2017Layout\Archive\d420889f-6aad-4ba4-99e4-ed7833795a10\Catalog.json
```

Lorsque vous exécutez cette commande, le programme d’installation analyse votre dossier de cache hors connexion pour trouver la liste des fichiers à supprimer. Vous avez ensuite la possibilité de revoir les fichiers qui vont être supprimés pour confirmer les suppressions.

## <a name="get-support-for-your-offline-installer"></a>Obtenir de l’aide pour votre programme d’installation hors connexion

Si vous rencontrez un problème avec votre installation hors connexion, nous voulons le savoir. Le meilleur moyen de nous en faire part est d’utiliser l’outil [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio.md). Lorsque vous utilisez cet outil, vous pouvez nous envoyer la télémétrie et des journaux, dont nous avons besoin pour nous aider à diagnostiquer et à résoudre le problème.

Nous offrons également une option de support par [**Conversation en direct**](https://visualstudio.microsoft.com/vs/support/#talktous) (en anglais uniquement) pour les problèmes liés à l’installation.

D’autres options de support sont également à votre disposition. Pour obtenir la liste, consultez notre page [Commentaires](../ide/feedback-options.md).

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio](install-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Outils de détection et de gestion des instances de Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](controlling-updates-to-visual-studio-deployments.md)
* [Maintenance et cycle de vie des produits Visual Studio](/visualstudio/releases/2019/servicing/)
