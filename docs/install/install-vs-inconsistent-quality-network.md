---
title: "Installer dans des environnements réseau à faible bande passante ou non fiables | Microsoft Docs"
description: "Décrit comment le programme d’installation de Visual Studio fonctionne dans des conditions réseau non fiables et explique comment télécharger les fichiers d’installation avant de commencer l’installation."
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 44DB1998-68CD-4560-870A-EE5B993DCF6E
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
ms.openlocfilehash: 9dbe70bce6c246416df64de304b06cd211320f2a
ms.contentlocale: fr-fr
ms.lasthandoff: 05/09/2017

---

# <a name="install-visual-studio-2017-on-low-bandwidth-or-unreliable-network-environments"></a>Installer Visual Studio 2017 dans des environnements réseau à faible bande passante ou non fiables
Nous avons conçu le nouveau programme d’installation de Visual Studio 2017 pour fonctionner correctement dans un large éventail de conditions réseau et informatiques.

- Les fichiers nécessaires à l’installation de Visual Studio étant distribués sur un réseau de distribution global, nous pouvons vous les faire parvenir à partir d’un serveur local.
- Pendant le processus d’installation, nous essayons trois technologies de téléchargement différentes (WebClient, BITS et WinInet) pour réduire les interférences avec le logiciel antivirus et proxy.
- Le nouveau modèle basé sur les charges de travail signifie que vous devez installer moins d’éléments qu’avec les versions antérieures de Visual Studio.

Par conséquent, nous vous recommandons d’essayer le nouveau programme d’installation web et nous pensons que vous allez apprécier l’expérience. Toutefois, si vous voulez être sûr d’avoir correctement téléchargé les fichiers d’installation avant de commencer l’installation de Visual Studio, nous avons tout prévu. Vous pouvez utiliser la ligne de commande pour créer un cache local des fichiers dont vous avez besoin avant de commencer l’installation.

Voici comment procéder.

## <a name="download-the-visual-studio-bootstrapper"></a>Télécharger le programme d’amorçage de Visual Studio
Commencez par télécharger le programme d’amorçage de Visual Studio pour l’édition de Visual Studio que vous avez choisie.

Le fichier de votre programme d’installation&mdash;ou pour être plus précis, un fichier de programme d’amorçage&mdash; correspond ou est semblable à l’une des valeurs suivantes.

| Édition                    | Fichier                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Communauté Visual Studio    | [vs_community.exe](https://aka.ms/vs/15/release/vs_community.exe)       |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)     |

## <a name="create-a-local-install-cache"></a>Créer un cache d’installation local
Pour créer une disposition locale, ouvrez une invite de commandes et utilisez l’une des commandes dans les exemples suivants. Ces exemples supposent que vous avez téléchargé le programme d’amorçage de Visual Studio Community : définissez la commande en fonction de votre édition.

- Pour le développement d’applications de bureau .NET et web .NET, exécutez :
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
  ```
- Pour le développement d’applications de bureau .NET et Office, exécutez :
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
  ```
- Pour le développement d’applications de bureau C++, exécutez :
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
  ```

- Pour créer une disposition locale complète avec toutes les fonctionnalités (cela prendra un certain temps, nous avons _beaucoup_ de fonctionnalités !), exécutez :
  ```
  vs_community.exe --layout c:\vs2017layout --lang en-US
  ```

Si vous souhaitez installer une langue autre que l’anglais, remplacez `en-US` par des paramètres régionaux dans la liste en bas de cette page. Utilisez cette [liste des composants et charges de travail disponibles](workload-and-component-ids.md) pour personnaliser davantage votre cache d’installation si nécessaire.

## <a name="install-from-the-local-cache"></a>Installer à partir du cache local
Quand vous procédez à l’exécution à partir d’un cache d’installation local, les versions locales de chacun de ces fichiers sont utilisées. Toutefois, si vous sélectionnez lors de l’installation des composants qui ne sont pas dans le cache, nous tentons de les télécharger à partir d’Internet.

Pour vérifier que vous installez uniquement les fichiers que vous avez téléchargés, utilisez les mêmes options de ligne de commande que celles utilisées pour créer le cache de disposition. Par exemple, si vous avez créé un cache de disposition avec la commande suivante :

```
vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

utilisez cette commande pour exécuter l’installation :

```
c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

## <a name="list-of-language-locales"></a>Liste des paramètres régionaux de langue
| **Paramètres régionaux de langue** | **Langue** |
| ----------------------- | --------------- |  
| cs-CZ | Tchèque |
| de-DE | Allemand |
| en-US | Anglais |
| es-ES | Espagnol |
| fr-FR | Français |
| it-IT | Italien |
| ja-JP | Japonais |
| ko-KR | Coréen |
| pl-PL | Polonais |
| pt-BR | Portugais - Brésil |
| ru-RU | Russe |
| tr-TR | Turc |
| zh-CN | Chinois (simplifié) |
| zh-TW | Chinois (traditionnel) |

## <a name="see-also"></a>Voir aussi
* [Installer Visual Studio](install-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)

