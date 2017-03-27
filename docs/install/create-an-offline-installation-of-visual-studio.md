---
title: "Créer un programme d’installation hors connexion pour Visual Studio 2017 | Microsoft Docs"
description: "Découvrez comment créer un programme d’installation hors connexion pour Visual Studio."
ms.custom: 
ms.date: 03/07/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- offline installer [Visual Studio]
- ISO [Visual Studio]
ms.assetid: 7bd7e724-7bfd-43f1-9935-981919be5a00
author: TerryGLee
ms.author: tglee
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
translationtype: Human Translation
ms.sourcegitcommit: 91fde66abf2f325ef0a6a0a2fd30e36981f44033
ms.openlocfilehash: acb47946c29d99cb53b34d67fe8a26f5611307f9
ms.lasthandoff: 03/08/2017

---
# <a name="create-an-offline-installer-for-visual-studio-2017"></a>Créer un programme d’installation hors connexion pour Visual Studio 2017 | Microsoft Docs
Nous savons que beaucoup de clients souhaitent un programme d’installation hors connexion pour [Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=844067). Bien que nous ne proposons pas d’image ISO, il est facile de créer un dossier que vous pouvez utiliser pour procéder à une installation hors connexion.

Voici comment procéder.

## <a name="download-the-setup-file-you-want"></a>Téléchargez le fichier d’installation souhaité
**[Télécharger](https://www.visualstudio.com/downloads?utm_source=mscom&utm_campaign=msdocs)** l’édition de Visual Studio souhaitée. Veillez à cliquer sur **Enregistrer**, puis cliquez sur **Ouvrir le dossier**.

Le fichier d’installation&mdash;ou pour être plus précis, un fichier de programme d’amorçage&mdash; correspond à une des valeurs suivantes.

|Édition | Fichier|  
|-------------|-----------------------|  
|Visual Studio Enterprise |**vs_enterprise.exe**|  
|Visual Studio Professional |**vs_professional.exe**|  
|Communauté Visual Studio |**vs_community.exe**|

## <a name="create-an-offline-installation-folder"></a>Créer un dossier d’installation hors connexion
Pour créer une installation hors connexion avec toutes les langues et toutes les fonctionnalités, utilisez une des commandes des exemples suivants.

Assurez-vous que vous exécutez la commande à partir de votre répertoire de téléchargement. En règle générale, il s’agit du répertoire `C:\Users\<username>\Downloads` sur un ordinateur exécutant Windows 10.

- Pour Visual Studio Enterprise, exécutez : <br>  ```vs_enterprise.exe --layout c:\vs2017offline```
- Pour Visual Studio Professional, exécutez : <br> ```vs_professional.exe --layout c:\vs2017offline```
- Pour Visual Studio Community, exécutez : <br> ```vs_community.exe --layout c:\vs2017offline```

Pour plus d’exemples, consultez la section [Comment personnaliser votre programme d’installation hors connexion](#how-to-customize-your-offline- installer) de cette page.

## <a name="install-from-the-offline-installation-folder"></a>Installer à partir du dossier d’installation hors connexion
Vous pouvez choisir d’exécuter le programme d’installation hors connexion maintenant ou ultérieurement. Dans les deux cas, procédez comme suit.

  1. Installez les certificats (ils se trouvent dans le dossier des Certificats se trouvant lui-même dans le dossier Disposition. Cliquez avec le bouton droit sur chacun d’eux et installez-les.

  2. Exécutez le fichier d’installation. Par exemple, exécutez : <br> ```c:\vs2017offline\vs_enterprise.exe```

## <a name="additional-tips-for-offline-installers"></a>Conseils supplémentaires pour les programmes d’installation hors connexion
Il est facile de personnaliser ou de mettre à jour votre programme d’installation hors connexion. Nous allons vous montrer comment procéder. En cas de problème lié à votre programme d’installation hors connexion, nous disposons également d’informations relatives au dépannage et à l’assistance.

### <a name="how-to-customize-your-offline-installer"></a>Comment personnaliser votre programme d’installation hors connexion
De nombreuses options vous permettent de personnaliser votre programme d’installation hors connexion. Voici quelques exemples montrant comment le personnaliser par [paramètre régional](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

 - Pour télécharger tous composants et les charges de travail dans une langue, exécutez : <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US```
 - Pour télécharger tous composants et les charges de travail de plusieurs langues, exécutez : <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP```
 - Pour télécharger une charge de travail pour toutes les langues, exécutez : <br> ```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure ```
 - Pour télécharger deux charges de travail et un composant facultatif dans trois langues, exécutez : <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure Microsoft.VisualStudio.Workload.ManagedDesktop Component.GitHub.VisualStudio --lang en-US de-DE ja-JP ``` Pour en savoir plus sur les options que vous pouvez utiliser pour personnaliser votre installation, consultez notre page [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017 ](use-command-line-parameters-to-install-visual-studio.md).


### <a name="how-to-update-an-offline-installer"></a>Comment mettre à jour un programme d’installation hors connexion
Vous voudrez peut-être mettre à jour votre programme d’installation hors connexion à une date ultérieure. Voici comment procéder.
* Pour mettre à jour une instance de Visual Studio que vous avez installée à partir d’un dossier d’installation hors connexion, exécutez le programme d’installation de Visual Studio, puis cliquez sur **Mettre à jour**.
* Pour actualiser votre dossier d’installation hors connexion de manière à inclure les dernières mises à jour, exécutez de nouveau la commande ```--layout```. Veillez à pointer vers le même dossier que celui utilisé auparavant ; de cette façon, seuls les composants mis à jour depuis la dernière exécution de ```--layout``` seront téléchargés.


Si vous souhaitez mettre à jour votre installation hors connexion, exécutez de nouveau la commande `--layout`. Veillez à pointer vers le même dossier que celui utilisé auparavant ; de cette façon, seuls les composants mis à jour depuis la dernière exécution de `--layout` seront téléchargés.

### <a name="how-to-troubleshoot-an-offline-installer"></a>Comment résoudre les problèmes d’un programme d’installation hors connexion
Parfois, des problèmes surgissent. Voici un tableau des problèmes connus et des solutions susceptibles de vous aider.

| Problème       | Élément                   | Solution |
| ----------- | ---------------------- | -------- |
| Vous recevez un message d’avertissement indiquant que l’installation de certains composants et packages est impossible.  | Programme d’installation du SDK Android (Niveau API) | Si vous souhaitez inclure des packages du Kit de développement logiciel Android SDK (niveau d’API), vous devez disposer d’une connexion Internet lorsque vous créez votre programme d’installation hors connexion. Si vous êtes sur un réseau limité, vous devez autoriser l’accès aux URL suivantes : <br><br> - http://dl.google.com:443 <br> - http://dl-ssl.google.com:443 <br>  - https://dl-ssl.google.com/android/repository/*<br><br>Pour plus d’informations sur la résolution des éventuels problèmes avec les paramètres de proxy, consultez le billet de blog [Visual Studio install failures (Android SDK Setup) behind a proxy](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) (Échec de l’installation de Visual Studio (Programme d’installation du SDK Android) derrière un proxy).  |  
| Les utilisateurs n’ont pas accès aux fichiers. | autorisations (ACL) | Vérifiez que vous ajustez les autorisations (ACL) de sorte qu’elles accordent un accès en lecture aux autres utilisateurs *avant* de partager l’installation hors connexion. |
| L’installation des nouvelles charges de travail, langues et des nouveaux composants a échoué.  | `--layout`  | Si vous effectuez l’installation à partir d’une disposition partielle et que vous sélectionnez des charges de travail, des composants ou des langues qui ne sont pas disponibles dans la disposition précédente, vérifiez que vous disposez d’une connexion à Internet. |

### <a name="how-to-get-support-for-your-offline-installer"></a>Comment obtenir de l’assistance pour votre programme d’installation hors connexion
Si vous rencontrez un problème avec votre installation hors connexion, nous voulons le savoir. Le meilleur moyen de nous en faire part est d’utiliser l’outil [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Lorsque vous utilisez cet outil, vous pouvez nous envoyer la télémétrie et des journaux, dont nous avons besoin pour nous aider à diagnostiquer et à résoudre le problème.

D’autres options de support sont également à votre disposition. Pour en obtenir la liste, consultez notre page [Nous contacter](../ide/how-to-report-a-problem-with-visual-studio-2017.md).


## <a name="see-also"></a>Voir aussi
* [Installer Visual Studio](install-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)

