---
title: "Créer une installation réseau de Visual Studio | Microsoft Docs"
description: "{{ESPACE RÉSERVÉ}}"
ms.date: 05/05/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
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
ms.openlocfilehash: c8c48a92ba4ba75e87d947364919688032842265
ms.contentlocale: fr-fr
ms.lasthandoff: 05/09/2017

---

# <a name="create-a-network-installation-of-visual-studio-2017"></a>Créer une installation réseau de Visual Studio 2017

En général, un administrateur d’entreprise crée un point d’installation réseau pour le déploiement sur les stations de travail clientes. Nous avons conçu Visual Studio 2017 pour vous permettre de mettre en cache les fichiers de l’installation initiale, ainsi que toutes les mises à jour de produit dans un dossier unique (opération parfois appelée _création d’une disposition_), de sorte que les stations de travail clientes peuvent utiliser le même emplacement réseau pour gérer leur installation, même si elles n’ont pas encore effectué la mise à jour de maintenance la plus récente.

> [!NOTE]
> Si vous utilisez plusieurs éditions de Visual Studio dans votre entreprise (par exemple, Visual Studio Professional et Visual Studio Enterprise), vous devez créer un partage d’installation réseau distinct pour chaque édition.

## <a name="download-the-visual-studio-bootstrapper"></a>Télécharger le programme d’amorçage de Visual Studio
**Téléchargez** l’édition de Visual Studio souhaitée. Veillez à cliquer sur **Enregistrer**, puis cliquez sur **Ouvrir le dossier**.

L’exécutable de votre programme d’installation&mdash;ou pour être plus précis, un fichier de programme d’amorçage&mdash; correspond à l’une des valeurs suivantes.

|Édition | Téléchargement|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://aka.ms/vs/15/release/vs_enterprise.exe) |
|Visual Studio Professional | [**vs_professional.exe**](https://aka.ms/vs/15/release/vs_professional.exe) |
|Communauté Visual Studio | [**vs_community.exe**](https://aka.ms/vs/15/release/vs_community.exe) |

Les autres programmes d’amorçage pris en charge incluent [vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe), [vs_feedbackclient.exe](https://aka.ms/vs/15/release/vs_feedbackclient.exe), [vs_teamexplorer.exe](https://aka.ms/vs/15/release/vs_teamexplorer.exe), [vs_testagent.exe](https://aka.ms/vs/15/release/vs_testagent.exe), [vs_testcontroller.exe](https://aka.ms/vs/15/release/vs_testcontroller.exe)et [vs_testprofessional.exe](https://aka.ms/vs/15/release/vs_testprofessional.exe).

## <a name="create-an-offline-installation-folder"></a>Créer un dossier d’installation hors connexion
Pour créer une installation hors connexion avec toutes les langues et toutes les fonctionnalités, utilisez une des commandes des exemples suivants.

Assurez-vous que vous exécutez la commande à partir de votre répertoire de téléchargement. En règle générale, il s’agit du répertoire `C:\Users\<username>\Downloads` sur un ordinateur exécutant Windows 10.

- Pour Visual Studio Enterprise, exécutez :
  ```
  vs_enterprise.exe --layout c:\vs2017offline
  ```
- Pour Visual Studio Professional, exécutez :
  ```
  vs_professional.exe --layout c:\vs2017offline
  ```
- Pour Visual Studio Community, exécutez :
  ```
  vs_community.exe --layout c:\vs2017offline
  ```

## <a name="modify-the-responsejson-file"></a>Modifier le fichier response.json
Vous pouvez modifier response.json pour définir les valeurs par défaut qui seront utilisées lors de l’exécution du programme d’installation.  Par exemple, vous pouvez configurer le fichier `response.json` pour sélectionner un ensemble spécifique de charges de travail sélectionnées automatiquement.
Pour plus d’informations, consultez [Automatiser l’installation de Visual Studio avec un fichier réponse](automated-installation-with-response-file.md).

## <a name="copy-the-layout-to-a-network-share"></a>Copier la disposition sur un partage réseau

Hébergez la disposition sur un partage réseau afin de pouvoir l’exécuter à partir d’autres ordinateurs.
* Exemple :<br>
```xcopy /e c:\vs2017offline \\server\products\VS2017```
    
## <a name="customizing-the-network-layout"></a>Personnalisation de la disposition réseau
Plusieurs options vous permettent de personnaliser votre disposition réseau. Vous pouvez créer une disposition partielle qui contient uniquement un ensemble spécifique de [paramètres régionaux de langue](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [charges de travail, composants et leurs dépendances recommandées ou facultatives](workload-and-component-ids.md). Cela peut être utile si vous savez que vous allez uniquement déployer un sous-ensemble des charges de travail sur les stations de travail clientes. Les paramètres de ligne de commande courants permettant de personnaliser la disposition incluent :

 - ```--add``` pour spécifier les [ID de charge de travail ou de composant](workload-and-component-ids.md).  Si `--add` est utilisé, seuls les composants et les charges de travail spécifiés avec `--add` sont téléchargés.  Si `--add` n’est pas utilisé, l’ensemble des charges de travail et composants est téléchargé.
 - ```--includeRecommended``` pour inclure tous les composants recommandés pour les ID de charge de travail spécifiés
 - ```--includeOptional``` pour inclure tous les composants recommandés et facultatifs pour les ID de charge de travail spécifiés.
 - ```--lang``` pour spécifier les [paramètres régionaux de langue](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).
 
Voici quelques exemples montrant comment créer une disposition partielle personnalisée.

 - Pour télécharger tous composants et les charges de travail dans une langue, exécutez : <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US```
 - Pour télécharger tous composants et les charges de travail de plusieurs langues, exécutez : <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP```
 - Pour télécharger une charge de travail pour toutes les langues, exécutez : <br> ```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --includeRecommended```
 - Pour télécharger deux charges de travail et un composant facultatif dans trois langues, exécutez : <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP ```
 - Pour télécharger deux charges de travail et tous leurs composants recommandés, exécutez : <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended ```
 - Pour télécharger deux charges de travail et tous leurs composants recommandés et facultatifs, exécutez : <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional ```


## <a name="deploying-from-a-network-installation"></a>Déploiement à partir d’une installation réseau
Les administrateurs peuvent déployer Visual Studio sur les stations de travail clientes dans le cadre d’un script d’installation. Les utilisateurs qui disposent de droits d’administrateur peuvent aussi exécuter le programme d’installation directement à partir du partage pour installer Visual Studio sur leur ordinateur.

- Les utilisateurs peuvent procéder à l’installation en exécutant : <br>```\\server\products\VS2017\vs_enterprise.exe```
- Les administrateurs peuvent procéder à l’installation en mode sans assistance en exécutant : <br>```\\server\products\VS2017\vs_enterprise.exe --quiet --wait --norestart```

> [!TIP]
> Quand elle est exécutée dans le cadre d’un fichier de commandes, l’option `--wait` garantit que le processus `vs_enterprise.exe` attend que l’installation soit terminée avant de retourner un code de sortie. Cela est utile quand un administrateur d’entreprise souhaite effectuer des actions supplémentaires sur l’installation terminée (par exemple, [appliquer une clé de produit à une installation réussie](automatically-apply-product-keys-when-deploying-visual-studio.md)), et qu’il est nécessaire d’attendre la fin de l’installation pour gérer le code de retour de cette installation.  Si vous n’utilisez pas `--wait`, le processus vs_enterprise.exe se termine avant que l’installation ne soit terminée et ne retourne pas un code de sortie précis qui représente l’état de l’installation.

### <a name="error-codes"></a>Codes d’erreur
Si vous avez utilisé le paramètre `--wait`, en fonction du résultat de l’opération, la variable d’environnement `%ERRORLEVEL%` a l’une des valeurs suivantes :

  | **Valeur** | **Résultat** |
  | --------- | ---------- |
  | 0 | Opération effectuée avec succès |
  | 3010 | Opération effectuée avec succès, mais l’installation nécessite un redémarrage avant de pouvoir être utilisée |
  | Autre | Une condition d’échec s’est produite - Pour plus d’informations, consultez les journaux |

## <a name="updating-a-network-install-layout"></a>Mise à jour d’une disposition d’installation réseau
Quand les mises à jour de produit deviennent disponibles, vous pouvez [mettre à jour la disposition d’installation réseau](update-a-network-installation-of-visual-studio.md) pour intégrer les packages mis à jour.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-2017-release"></a>Comment créer une disposition pour une version antérieure de Visual Studio 2017
**Remarque** : Les programmes d’amorçage de VS 2017 disponibles sur http://www.visualstudio.com téléchargent et installent la dernière version de Visual Studio 2017 disponible chaque fois qu’ils sont exécutés. Si vous téléchargez un programme d’amorçage de Visual Studio aujourd’hui et l’exécutez pendant 6 mois à partir de maintenant, il installe la version de Visual Studio 2017 disponible à ce moment-là. Si vous créez une disposition, l’installation de Visual Studio à partir de cette disposition installe la version spécifique de VS qui existe dans la disposition. Même si une version plus récente peut exister en ligne, vous obtenez la version de Visual Studio qui se trouve dans la disposition.

Si vous devez créer une disposition pour une ancienne version de Visual Studio 2017, vous pouvez accéder à https://my.visualstudio.com pour télécharger des versions « définitives » des programmes d’amorçage de Visual Studio 2017 pour les versions prises en charge, ce qui vous permet de créer une disposition d’installation réseau pour cette ancienne version. 

### <a name="how-to-get-support-for-your-offline-installer"></a>Comment obtenir de l’assistance pour votre programme d’installation hors connexion
Si vous rencontrez un problème avec votre installation hors connexion, nous voulons le savoir. Le meilleur moyen de nous en faire part est d’utiliser l’outil [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Lorsque vous utilisez cet outil, vous pouvez nous envoyer la télémétrie et des journaux, dont nous avons besoin pour nous aider à diagnostiquer et à résoudre le problème.

D’autres options de support sont également à votre disposition. Pour en obtenir la liste, consultez notre page [Nous contacter](../ide/how-to-report-a-problem-with-visual-studio-2017.md).

## <a name="see-also"></a>Voir aussi
* [Installer Visual Studio](install-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)

