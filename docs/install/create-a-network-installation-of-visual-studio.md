---
title: Créer une installation réseau de Visual Studio
description: Découvrez comment créer un point d’installation réseau pour le déploiement de Visual Studio en entreprise.
ms.date: 10/17/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6fdecc141affcb88d0a04346767469ef5296557d
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
---
# <a name="create-a-network-installation-of-visual-studio-2017"></a>Créer une installation réseau de Visual Studio 2017

En général, un administrateur d’entreprise crée un point d’installation réseau pour le déploiement sur les stations de travail clientes. Nous avons conçu Visual Studio 2017 pour que vous puissiez mettre en cache dans un dossier unique les fichiers de l’installation initiale avec toutes les mises à jour de produit. (Ce processus est également appelé _création d’une disposition_.) De cette façon, les stations de travail clientes peuvent utiliser le même emplacement réseau pour gérer leur installation, même si elles n’ont pas encore effectué leur dernière mise à jour de maintenance.

 > [!NOTE]
 > Si plusieurs éditions de Visual Studio sont utilisées dans votre entreprise (par exemple, Visual Studio Professional et Visual Studio Enterprise), vous devez créer un partage d’installation réseau distinct pour chaque édition.

## <a name="download-the-visual-studio-bootstrapper"></a>Télécharger le programme d’amorçage de Visual Studio

**Téléchargez** l’édition de Visual Studio souhaitée. Veillez à cliquer sur **Enregistrer**, puis cliquez sur **Ouvrir le dossier**.

L’exécutable de votre programme d’installation, ou pour être plus précis le fichier du programme d’amorçage, doit correspond à l’un de ceux mentionnés ici.

|Édition | Téléchargement|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://aka.ms/vs/15/release/vs_enterprise.exe) |
|Visual Studio Professional | [**vs_professional.exe**](https://aka.ms/vs/15/release/vs_professional.exe) |
|Communauté Visual Studio | [**vs_community.exe**](https://aka.ms/vs/15/release/vs_community.exe) |

Les autres programmes d’amorçage pris en charge incluent [vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe), [vs_feedbackclient.exe](https://aka.ms/vs/15/release/vs_feedbackclient.exe), [vs_teamexplorer.exe](https://aka.ms/vs/15/release/vs_teamexplorer.exe), [vs_testagent.exe](https://aka.ms/vs/15/release/vs_testagent.exe), [vs_testcontroller.exe](https://aka.ms/vs/15/release/vs_testcontroller.exe)et [vs_testprofessional.exe](https://aka.ms/vs/15/release/vs_testprofessional.exe).

## <a name="create-an-offline-installation-folder"></a>Créer un dossier d’installation hors connexion

Vous devez avoir une connexion Internet pour effectuer cette étape. Pour créer une installation hors connexion avec toutes les langues et toutes les fonctionnalités, utilisez une des commandes des exemples suivants.

   > [!IMPORTANT]
   > Une disposition Visual Studio 2017 complète nécessite au moins 35 Go d’espace disque et peut être assez longue à télécharger.  Consultez la section [Personnaliser la disposition du réseau](#customizing-the-network-layout) pour savoir plus en détails comment créer une disposition comprenant uniquement les composants que vous souhaitez installer.
   >
   > [!TIP]
   > Vérifiez que vous exécutez la commande à partir de votre répertoire de téléchargement. En règle générale, il s’agit du répertoire `C:\Users\<username>\Downloads` sur un ordinateur exécutant Windows 10.

- Pour Visual Studio Enterprise, exécutez :

  ```vs_enterprise.exe --layout c:\vs2017offline```

- Pour Visual Studio Professional, exécutez :

  ```vs_professional.exe --layout c:\vs2017offline```

- Pour Visual Studio Community, exécutez :

  ```vs_community.exe --layout c:\vs2017offline```

## <a name="modify-the-responsejson-file"></a>Modifier le fichier response.json

Vous pouvez modifier response.json pour définir les valeurs par défaut qui sont utilisées lors de l’exécution du programme d’installation.  Par exemple, vous pouvez configurer le fichier `response.json` pour sélectionner un ensemble spécifique de charges de travail sélectionnées automatiquement.
Pour plus d’informations, consultez [Automatiser l’installation de Visual Studio avec un fichier réponse](automated-installation-with-response-file.md).

## <a name="copy-the-layout-to-a-network-share"></a>Copier la disposition sur un partage réseau

Hébergez la disposition sur un partage réseau afin de pouvoir l’exécuter à partir d’autres ordinateurs.
* Exemple :<br>
```xcopy /e c:\vs2017offline \\server\products\VS2017```

## <a name="customizing-the-network-layout"></a>Personnalisation de la disposition réseau

Plusieurs options vous permettent de personnaliser votre disposition réseau. Vous pouvez créer une disposition partielle qui contient uniquement un ensemble spécifique de [paramètres régionaux de langue](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [charges de travail, composants et leurs dépendances recommandées ou facultatives](workload-and-component-ids.md). Cela est peut-être utile si vous savez que vous allez uniquement déployer un sous-ensemble de charges de travail sur les stations de travail clientes. Les paramètres de ligne de commande standard permettant de personnaliser la disposition incluent :

* ```--add``` pour spécifier les [ID de charge de travail ou de composant](workload-and-component-ids.md).  Si `--add` est utilisé, seuls les composants et les charges de travail spécifiés avec `--add` sont téléchargés.  Si `--add` n’est pas utilisé, l’ensemble des charges de travail et des composants est téléchargé.
* ```--includeRecommended``` pour inclure tous les composants recommandés pour les ID de charge de travail spécifiés
* ```--includeOptional``` pour inclure tous les composants recommandés et facultatifs pour les ID de charge de travail spécifiés.
* ```--lang``` pour spécifier les [paramètres régionaux de langue](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Voici quelques exemples montrant comment créer une disposition partielle personnalisée.

* Pour télécharger tous composants et les charges de travail dans une langue, exécutez : <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US```
* Pour télécharger tous composants et les charges de travail de plusieurs langues, exécutez : <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP```
* Pour télécharger une charge de travail pour toutes les langues, exécutez : <br> ```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --includeRecommended```
* Pour télécharger deux charges de travail et un composant facultatif dans trois langues, exécutez : <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP ```
* Pour télécharger deux charges de travail et tous leurs composants recommandés, exécutez : <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended ```
* Pour télécharger deux charges de travail et tous leurs composants recommandés et facultatifs, exécutez : <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional ```

### <a name="new-in-153"></a>Nouveautés de la version 15.3

Lorsque vous exécutez une commande de disposition, les options que vous spécifiez sont enregistrées (par exemple, les langues et les charges de travail). Les commandes de disposition suivantes englobent toutes les options précédentes.  Voici un exemple de disposition avec une charge de travail pour l’anglais uniquement :

```vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US```

Lorsque vous souhaitez mettre à jour cette disposition vers une version plus récente, vous n’avez pas à spécifier de paramètres de ligne de commande supplémentaires. Les paramètres précédents sont enregistrés et utilisés par toutes les commandes de disposition suivantes dans ce dossier de disposition.  La commande suivante met à jour la disposition partielle existante.

```vs_enterprise.exe --layout c:\VS2017Layout```

Lorsque vous voulez ajouter une charge de travail supplémentaire, suivez cet exemple qui montre comment faire. Dans ce cas, nous allons ajouter une langue localisée et la charge de travail Azure.  À présent, Managed Desktop et Azure sont inclus dans cette disposition.  Les ressources de langue pour l’anglais et l’allemand sont comprises pour toutes ces charges de travail. La disposition est mise à jour avec la dernière version disponible.

```vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE```

Si vous souhaitez passer d’une disposition existante à une disposition complète, utilisez l’option --all, comme indiqué dans l’exemple suivant.

```vs_enterprise.exe --layout c:\VS2017Layout --all```

## <a name="deploying-from-a-network-installation"></a>Déploiement à partir d’une installation réseau

Les administrateurs peuvent déployer Visual Studio sur les stations de travail clientes dans le cadre d’un script d’installation. Les utilisateurs qui disposent de droits d’administrateur peuvent aussi exécuter le programme d’installation directement à partir du partage pour installer Visual Studio sur leur ordinateur.

- Les utilisateurs peuvent procéder à l’installation en exécutant : <br>```\\server\products\VS2017\vs_enterprise.exe```
- Les administrateurs peuvent procéder à l’installation en mode sans assistance en exécutant : <br>```\\server\products\VS2017\vs_enterprise.exe --quiet --wait --norestart```

> [!TIP]
> Quand elle est exécutée dans le cadre d’un fichier de commandes, l’option `--wait` garantit que le processus `vs_enterprise.exe` attend que l’installation soit terminée avant de retourner un code de sortie. C’est utile si un administrateur d’entreprise souhaite effectuer d’autres opérations sur une installation terminée (par exemple, pour [appliquer une clé de produit sur une installation réussie](automatically-apply-product-keys-when-deploying-visual-studio.md)), alors qu’il doit attendre que l’installation se termine pour gérer le code de retour de cette installation.  Si vous n’utilisez pas `--wait`, le processus `vs_enterprise.exe` s’arrête avant que l’installation soit terminée et retourne un code de sortie incorrect qui ne représente pas l’état de l’opération d’installation.

Lorsque vous installez à partir d’une disposition, le contenu qui est installé est acquis à partir de la disposition. Toutefois, si vous sélectionnez un composant qui ne se trouve pas dans la disposition, celui-ci est téléchargé à partir d’Internet.  Si vous voulez empêcher le programme d’installation de Visual Studio de télécharger le contenu manquant dans la disposition, utilisez l’option `--noWeb`.  Si `--noWeb` est utilisé et qu’un contenu à installer est absent de la disposition, l’installation échoue.  

### <a name="error-codes"></a>Codes d’erreur

Si vous avez utilisé le paramètre `--wait`, en fonction du résultat de l’opération, la variable d’environnement `%ERRORLEVEL%` a l’une des valeurs suivantes :

  | **Valeur** | **Résultat** |
  | --------- | ---------- |
  | 0 | Opération effectuée avec succès |
  | 3010 | Opération effectuée avec succès, mais l’installation nécessite un redémarrage avant de pouvoir être utilisée |
  | Autre | Une condition d’échec s’est produite - Pour plus d’informations, consultez les journaux |

## <a name="updating-a-network-install-layout"></a>Mise à jour d’une disposition d’installation réseau

Quand les mises à jour de produit deviennent disponibles, vous avez la possibilité de [mettre à jour la disposition d’installation réseau](update-a-network-installation-of-visual-studio.md) pour intégrer les packages mis à jour.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-2017-release"></a>Comment créer une disposition pour une version antérieure de Visual Studio 2017

> [!NOTE]
> Les programmes d’amorçage de Visual Studio 2017 qui sont disponibles sur [VisualStudio.com](http://www.visualstudio.com) téléchargent et installent la dernière version de Visual Studio 2017 disponible chaque fois qu’ils sont exécutés. Si vous téléchargez un programme d’amorçage de Visual Studio aujourd’hui et que vous l’exécutez pendant six mois à partir de maintenant, celui-ci installe la version de Visual Studio 2017 disponible à ce moment-là. Si vous créez une disposition, l’installation de Visual Studio à partir de cette disposition installe la version spécifique de Visual Studio qui existe dans la disposition. Même si une version plus récente peut exister en ligne, vous obtenez la version de Visual Studio qui se trouve dans la disposition.

Si vous devez créer une disposition pour une version antérieure de Visual Studio 2017, vous pouvez accéder à https://my.visualstudio.com et télécharger les versions « corrigées » des programmes d’amorçage de Visual Studio 2017.

### <a name="how-to-get-support-for-your-offline-installer"></a>Comment obtenir de l’assistance pour votre programme d’installation hors connexion

Si vous rencontrez un problème avec votre installation hors connexion, nous voulons le savoir. Le meilleur moyen de nous en faire part est d’utiliser l’outil [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Lorsque vous utilisez cet outil, vous pouvez nous envoyer la télémétrie et des journaux, dont nous avons besoin pour nous aider à diagnostiquer et à résoudre le problème.

D’autres options de support sont également à votre disposition. Pour en obtenir la liste, consultez notre page [Nous contacter](../ide/how-to-report-a-problem-with-visual-studio-2017.md).

## <a name="get-support"></a>Obtenir de l’aide

Parfois, des problèmes peuvent se produire. Si votre installation de Visual Studio échoue, consultez la page [Résolution des problèmes d’installation et de mise à niveau de Visual Studio 2017](troubleshooting-installation-issues.md). Si aucune étape de résolution des problèmes ne vous aide, vous pouvez nous contacter pour une conversation en direct sur une assistance à l’installation (en anglais uniquement). Pour plus de détails, consultez la [page du support Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Voici d’autres options de support :

* Vous pouvez nous signaler des problèmes au niveau d’un produit via l’outil [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio-2017.md) qui s’affiche dans le programme d’installation de Visual Studio et dans l’IDE de Visual Studio.
* Vous pouvez nous faire part d’une suggestion de produit via [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Vous pouvez suivre les problèmes au niveau d’un produit et obtenir des réponses dans la [Communauté des développeurs Visual Studio](https://developercommunity.visualstudio.com/).
* Vous pouvez également communiquer avec nous et d’autres développeurs Visual Studio en prenant part à notre [conversation Visual Studio dans la communauté Gitter](https://gitter.im/Microsoft/VisualStudio). (Cette option nécessite un compte [GitHub](https://github.com/).)

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio](install-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
