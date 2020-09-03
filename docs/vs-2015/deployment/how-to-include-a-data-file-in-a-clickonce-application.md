---
title: 'Comment : inclure un fichier de données dans une application ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 9120a5b3cb60f6c607ed97ab2df24bb157c72371
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153765"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Comment : inclure un fichier de données dans une application ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chaque [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application que vous installez se voit attribuer un répertoire de données sur le disque local de l’ordinateur de destination, où l’application peut gérer ses propres données. Les fichiers de données peuvent inclure des fichiers de n’importe quel type : fichiers texte, fichiers XML ou même fichiers de base de données Microsoft Access (. mdb). Les procédures suivantes vous montrent comment ajouter un fichier de données de n’importe quel type dans votre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application.  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>Pour inclure un fichier de données à l’aide de Mage.exe  
  
1. Ajoutez le fichier de données à votre répertoire d’application avec le reste des fichiers de votre application.  
  
    En règle générale, le répertoire de votre application est un répertoire étiqueté avec la version actuelle du déploiement, par exemple, v 1.0.0.0.  
  
2. Mettez à jour le manifeste de votre application pour répertorier le fichier de données.  
  
    **mage-u v 1.0.0.0 \ application. manifest-FromDirectory v 1.0.0.0**  
  
    Cette tâche permet de recréer la liste des fichiers dans le manifeste de votre application et de générer automatiquement les signatures de hachage.  
  
3. Ouvrez le manifeste de l’application dans votre éditeur de texte ou XML préféré et recherchez l' `file` élément correspondant à votre fichier récemment ajouté.  
  
    Si vous avez ajouté un fichier XML nommé `Data.xml` , le fichier doit ressembler à l’exemple de code suivant.  
  
   `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
4. Ajoutez l’attribut `type` à cet élément et fournissez-lui la valeur `data` .  
  
   `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
5. Signez à nouveau votre manifeste d’application à l’aide de votre paire de clés ou certificat, puis resignez votre manifeste de déploiement.  
  
    Vous devez signer à nouveau votre manifeste de déploiement, car son hachage du manifeste de l’application a changé.  
  
    **fichier manifeste de l’application mage-s-CF cert_file-mot de passe**  
  
    **manifeste de déploiement mage-u-manifeste de l’application APPM**  
  
    **mage-s-manifeste de déploiement-CF CertFile-pwd mot_de_passe**  
  
6. 
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Pour inclure un fichier de données à l’aide de MageUI.exe  
  
1. Ajoutez le fichier de données à votre répertoire d’application avec le reste des fichiers de votre application.  
  
2. En règle générale, le répertoire de votre application est un répertoire étiqueté avec la version actuelle du déploiement, par exemple, v 1.0.0.0.  
  
3. Dans le menu **fichier** , cliquez sur **ouvrir** pour ouvrir le manifeste de votre application.  
  
4. Sélectionnez l’onglet **fichiers** .  
  
5. Dans la zone de texte en haut de l’onglet, entrez le répertoire qui contient les fichiers de votre application, puis cliquez sur **remplir**.  
  
     Votre fichier de données s’affiche dans la grille.  
  
6. Définissez la valeur de **type de fichier** du fichier de données sur **données**.  
  
7. Enregistrez le manifeste de l’application, puis signez à nouveau le fichier.  
  
     MageUI.exe vous invite à signer à nouveau le fichier.  
  
8. Signer à nouveau votre manifeste de déploiement  
  
     Vous devez signer à nouveau votre manifeste de déploiement, car son hachage du manifeste de l’application a changé.  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux données locales et distantes dans les applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
