---
title: 'Comment : inclure un fichier de données dans une Application ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 5e954550b8d59f1d1672e1229387714ad251a38c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204696"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Comment : inclure un fichier de données dans une application ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chaque [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application que vous installez est affectée à un répertoire de données sur le disque local de l’ordinateur de destination dans lequel l’application peut gérer ses propres données. Fichiers de données peuvent inclure n’importe quel type de fichiers : fichiers texte, fichiers XML ou même Microsoft Access (.mdb) de la base de données. Les procédures suivantes vous montrent comment ajouter un fichier de données de n’importe quel type dans votre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application.  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>Pour inclure un fichier de données à l’aide de Mage.exe  
  
1.  Ajouter le fichier de données à votre répertoire de l’application avec le reste des fichiers de votre application.  
  
     En règle générale, le répertoire de votre application sera un répertoire étiqueté avec la version actuelle du déploiement, par exemple, v1.0.0.0.  
  
2.  Mettre à jour votre manifeste d’application vers le fichier de données de liste.  
  
     **Mage -u v1.0.0.0\Application.manifest - FromDirectory v1.0.0.0**  
  
     Pour effectuer cette tâche permet de recréer la liste des fichiers dans votre manifeste d’application et génère aussi automatiquement les signatures de hachage.  
  
3.  Ouvrez le manifeste d’application dans votre texte favori ou votre éditeur XML et recherchez le `file` élément pour votre fichier récemment ajouté.  
  
     Si vous avez ajouté un fichier XML nommé `Data.xml`, le fichier doit ressembler à l’exemple de code suivant.  
  
 `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Ajoutez l’attribut `type` à cet élément et lui fournir une valeur de `data`.  
  
 `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Signer à nouveau votre manifeste d’application à l’aide de votre paire de clés ou un certificat et signer à nouveau votre manifeste de déploiement.  
  
     Vous devez resigner votre manifeste de déploiement, car son hachage du manifeste d’application a changé.  
  
     **mot de passe - cf cert_file - pwd le manifeste d’application -s de Mage**  
  
     **manifeste de l’application appm manifeste - déploiement -u Mage**  
  
     **mot de passe - pwd cf - certfile de manifeste de déploiement de s - Mage**  
  
2.  
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Pour inclure un fichier de données à l’aide de MageUI.exe  
  
1.  Ajouter le fichier de données à votre répertoire de l’application avec le reste des fichiers de votre application.  
  
2.  En règle générale, le répertoire de votre application sera un répertoire étiqueté avec la version actuelle du déploiement, par exemple, v1.0.0.0.  
  
3.  Sur le **fichier** menu, cliquez sur **ouvrir** pour ouvrir votre manifeste d’application.  
  
4.  Sélectionnez le **fichiers** onglet.  
  
5.  Dans la zone de texte en haut de l’onglet, entrez le répertoire qui contient les fichiers de votre application, puis cliquez sur **Populate**.  
  
     Votre fichier de données s’affiche dans la grille.  
  
6.  Définir le **Type de fichier** valeur du fichier de données à **données**.  
  
7.  Enregistrez le manifeste d’application et signer à nouveau le fichier.  
  
     MageUI.exe vous invite à resigner le fichier.  
  
8.  Signer à nouveau votre manifeste de déploiement  
  
     Vous devez resigner votre manifeste de déploiement, car son hachage du manifeste d’application a changé.  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux données locales et distantes dans les applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)



