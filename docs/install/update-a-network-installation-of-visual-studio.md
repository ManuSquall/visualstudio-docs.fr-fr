---
title: Mettre à jour une installation réseau
description: Découvrez comment mettre à jour une installation réseau de Visual Studio à l’aide de la commande --layout
ms.date: 2/22/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a59bbac5140e4267a52847a2152862057ce24210
ms.sourcegitcommit: 1c8e07b98fc0a44b5ab90bcef77d9fac7b3eb452
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2019
ms.locfileid: "56796632"
---
# <a name="update-a-network-based-installation-of-visual-studio-2017"></a>Mettre à jour une installation réseau de Visual Studio 2017

Il est possible de mettre à jour une disposition d’installation réseau de Visual Studio avec les dernières mises à jour de produit, afin de pouvoir l’utiliser comme point d’installation de la dernière mise à jour de Visual Studio, et pour gérer aussi les installations déjà déployées sur les stations de travail clientes.

## <a name="how-to-update-a-network-layout"></a>Comment mettre à jour une disposition réseau

Pour actualiser le partage d’installation réseau et inclure les dernières mises à jour, exécutez la commande `--layout` pour télécharger de manière incrémentielle les packages mis à jour.

**Nouveautés de la version 15.3** : Si vous avez sélectionné une disposition partielle lors de la création de la disposition réseau, ces paramètres sont enregistrés.  Toutes les commandes de disposition futures utilisent les options précédentes ainsi que toutes les nouvelles options que vous indiquez. Si vous vous servez d’une disposition d’une version antérieure, vous devez utiliser les mêmes paramètres de ligne de commande que ceux que vous avez utilisés quand vous avez créé la disposition d’installation réseau (autrement dit, les mêmes charges de travail et langues) pour mettre à jour son contenu.

Si vous hébergez une disposition sur un partage de fichiers, vous devez mettre à jour une copie privée de la disposition (par exemple, c:\vs2017offline) et, une fois que tout le contenu mis à jour est téléchargé, la copier sur votre partage de fichiers (par exemple, \\serveur\produits\VS2017). Si vous ne le faites pas, il est très probable que les utilisateurs exécutant le programme d’installation pendant que vous mettez à jour la disposition ne soient pas en mesure de récupérer tout le contenu de la disposition, puisque celui-ci n’est pas encore totalement à jour.

Intéressons-nous de plus près à quelques exemples de création et de mise à jour d’une disposition :

* Tout d’abord, voyons un exemple montrant comment créer une disposition avec une charge de travail pour l’anglais uniquement :

  ```cmd
  vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
  ```

* Voici comment mettre à jour cette même disposition vers une version plus récente. Vous n’êtes pas obligé de spécifier les paramètres de ligne de commande supplémentaires. Les paramètres précédents étaient enregistrés et ils vont être utilisés par toutes les commandes de disposition suivantes dans ce dossier de disposition.

  ```cmd
  vs_enterprise.exe --layout c:\VS2017Layout
  ```

* Voici comment mettre à jour votre disposition avec une version plus récente en mode sans assistance. L’opération de disposition exécute le processus d’installation dans une nouvelle fenêtre de console. La fenêtre reste ouverte pour que les utilisateurs puissent voir le résultat final, ainsi qu’un récapitulatif des erreurs qui se sont produites. Si vous effectuez une opération de disposition en mode sans assistance (par exemple, si vous avez un script qui est exécuté régulièrement pour mettre à jour votre disposition vers la version la plus récente), utilisez le paramètre `--passive` pour que le processus ferme automatiquement la fenêtre.

  ```cmd
  vs_enterprise.exe --layout c:\VS2017Layout --passive
  ```

* Voici comment ajouter une charge de travail supplémentaire et une langue localisée.  (Cette commande ajoute la charge de travail Azure.)  À présent, Managed Desktop et Azure sont inclus dans cette disposition.  Les ressources de langue pour l’anglais et l’allemand sont également englobées pour toutes ces charges de travail.  De plus, la disposition est mise à jour avec la dernière version disponible.

  ```cmd
  vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
  ```

    > [!IMPORTANT]
    > Une opération de mise à jour n’installe pas les derniers composants facultatifs ajoutés, même si vous les incluez dans une section d’« ajout » du [fichier réponse](automated-installation-with-response-file.md). Cela est dû au fait que l’opération d’ajout n’est pas utilisée durant une mise à jour.<br>
    > **Solution de contournement** : Exécutez une opération de modification distincte, après une mise à niveau, pour installer les composants manquants.

* Et pour finir, voici comment ajouter une charge de travail et une langue localisée supplémentaires sans mettre à jour la version. (Cette commande ajoute la charge de travail ASP.NET & Web.)  Désormais, les charges de travail Managed Desktop, Azure et ASP.NET & Web sont incluses dans cette disposition. Les ressources de langue pour l’anglais, l’allemand et le français sont également englobées pour toutes ces charges de travail.  Toutefois, la disposition n’a été pas mise à jour vers la toute dernière version disponible lors de l’exécution de cette commande. Elle reste à la version existante.

  ```cmd
  vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
  ```

## <a name="how-to-deploy-an-update-to-client-machines"></a>Comment déployer une mise à jour sur les ordinateurs clients

Selon la configuration de votre environnement réseau, une mise à jour peut être déployée par un administrateur d’entreprise ou lancée à partir d’un ordinateur client.

* Les utilisateurs peuvent mettre à jour une instance de Visual Studio qui a été installée à partir d’un dossier d’installation hors connexion :
  * Exécutez le programme d’installation de Visual Studio.
  * Cliquez ensuite sur **Mettre à jour**.

* Les administrateurs peuvent mettre à jour les déploiements de clients de Visual Studio sans aucune intervention utilisateur avec deux commandes distinctes :
  * Mettez tout d’abord à jour Visual Studio Installer : <br>```vs_enterprise.exe --quiet --update```
  * Mettez ensuite à jour l’application Visual Studio proprement dite : <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

> [!NOTE]
> Utilisez la [commande vswhere.exe](tools-for-managing-visual-studio-instances.md) pour identifier le chemin d’installation d’une instance existante de Visual Studio sur un ordinateur client.
>
> [!TIP]
> Pour plus d’informations sur le contrôle du moment de la présentation des notifications de mise à jour aux utilisateurs, consultez [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](controlling-updates-to-visual-studio-deployments.md).

## <a name="how-to-verify-a-layout"></a>Comment vérifier une disposition

Utilisez l’option `--verify` pour effectuer la vérification dans le cache hors connexion fourni. Elle contrôle si des fichiers de package sont manquants ou non valides. À la fin de la vérification, la liste des fichiers manquants et non valides est imprimée.

```cmd
vs_enterprise.exe --layout <layoutDir> --verify
```

Le fichier vs_enterprise.exe peut être appelé à l’intérieur du répertoire layoutDir.

> [!NOTE]
> Certains fichiers de métadonnées importantes, qui sont nécessaires à l’option `--verify`, doivent se trouver dans le cache hors connexion de la disposition. Si ces fichiers de métadonnées sont manquants, "--verify" ne peut pas s’exécuter et le programme d’installation signale une erreur. Si vous rencontrez cette erreur, recréez une nouvelle disposition en mode hors connexion dans un dossier différent (ou dans le même dossier de cache hors connexion). Pour cela, exécutez la même commande de disposition que celle que vous avez utilisée pour créer la disposition hors connexion initiale. Par exemple, `Vs_enterprise.exe --layout <layoutDir>`.

Comme Microsoft fournit régulièrement des mises à jour de Visual Studio, la version de la nouvelle disposition que vous créez peut donc être différente de celle de la disposition initiale.

## <a name="how-to-fix-a-layout"></a>Comment corriger une disposition

Utilisez `--fix` pour effectuer la même vérification que `--verify` et pour tenter également de résoudre les problèmes identifiés. Le processus `--fix` nécessite une connexion Internet, ainsi vous devez vous assurer que votre ordinateur est connecté à Internet avant d’appeler `--fix`.

```cmd
vs_enterprise.exe --layout <layoutDir> --fix
```

Le fichier vs_enterprise.exe peut être appelé à l’intérieur du répertoire layoutDir.

## <a name="how-to-remove-older-versions-from-a-layout"></a>Comment supprimer les versions antérieures d’une disposition

Suite aux mises à jour de disposition que vous avez effectuées vers un cache hors connexion, le dossier du cache de disposition peut contenir quelques packages obsolètes qui ne sont plus utiles à la dernière installation en date de Visual Studio. Vous pouvez utiliser l’option `--clean` pour supprimer les packages obsolètes à partir d’un dossier de cache hors connexion.

Pour ce faire, vous avez besoin du chemin de fichier du ou des manifestes de catalogue qui contiennent les packages obsolètes. Vous pouvez trouver les manifestes de catalogue dans un dossier Archive situé dans le cache de disposition en mode hors connexion. Ils sont enregistrés à cet endroit lorsque vous mettez à jour une disposition. Dans le dossier Archive, il existe un ou plusieurs dossiers nommés GUID qui contiennent chacun un manifeste de catalogue obsolète. Le nombre de dossiers GUID doit être le même que le nombre de mises à jour apportées à votre cache hors connexion.

Quelques fichiers sont enregistrés à l’intérieur de chaque dossier GUID. Les deux fichiers les plus intéressants sont « catalog.json » et « version.txt ». Le fichier catalog.json est le manifeste de catalogue obsolète que vous devez passer à l’option `--clean`. L’autre fichier, version.txt, contient la version de ce manifeste de catalogue obsolète. En fonction du numéro de version, vous pouvez décider de supprimer ou non les packages obsolètes à partir de ce manifeste de catalogue. Vous pouvez en faire de même lorsque vous parcourez les autres dossiers GUID. Après avoir décidé du ou des catalogues à nettoyer, exécutez la commande `--clean` en spécifiant les chemins de fichier de ces catalogues.

Voici quelques exemples montrant comment utiliser l’option--clean :

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> <file-path-of-catalog2> …
```

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> --clean <file-path-of-catalog2> …
```

Vous pouvez aussi appeler le fichier vs_enterprise.exe à l’intérieur du répertoire &lt;layoutDir&gt;. Voici un exemple :

```cmd
c:\VS2017Layout\vs_enterprise.exe --layout c:\VS2017Layout --clean c:\VS2017Layout\Archive\1cd70189-fc55-4583-8ad8-a2711e928325\Catalog.json --clean c:\VS2017Layout\Archive\d420889f-6aad-4ba4-99e4-ed7833795a10\Catalog.json
```

Lorsque vous exécutez cette commande, le programme d’installation analyse votre dossier de cache hors connexion pour trouver la liste des fichiers à supprimer. Vous avez ensuite la possibilité de revoir les fichiers qui vont être supprimés pour confirmer les suppressions.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio](install-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Outils de détection et de gestion des instances de Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](controlling-updates-to-visual-studio-deployments.md)
