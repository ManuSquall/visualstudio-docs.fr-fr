---
title: 'Procédure : Inclure un fichier de données dans une Application ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 673b22dfbde5497f6be7b24bf04773f6cddf4a01
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999663"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Procédure : Inclure un fichier de données dans une application ClickOnce
Chaque [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application que vous installez est affectée à un répertoire de données sur le disque local de l’ordinateur de destination dans lequel l’application peut gérer ses propres données. Fichiers de données peuvent inclure n’importe quel type de fichiers : fichiers texte, fichiers XML ou même base de données Microsoft Access (*.mdb*) les fichiers. Les procédures suivantes vous montrent comment ajouter un fichier de données de n’importe quel type dans votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application.  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>Pour inclure un fichier de données à l’aide de Mage.exe  
  
1. Ajouter le fichier de données à votre répertoire de l’application avec le reste des fichiers de votre application.  
  
    En règle générale, le répertoire de votre application sera un répertoire étiqueté avec la version actuelle du déploiement, par exemple, v1.0.0.0.  
  
2. Mettre à jour votre manifeste d’application vers le fichier de données de liste.  
  
    `mage -u v1.0.0.0\Application.manifest -FromDirectory v1.0.0.0`  
  
    Pour effectuer cette tâche permet de recréer la liste des fichiers dans votre manifeste d’application et génère aussi automatiquement les signatures de hachage.  
  
3. Ouvrez le manifeste d’application dans votre texte favori ou votre éditeur XML et recherchez le `file` élément pour votre fichier récemment ajouté.  
  
    Si vous avez ajouté un fichier XML nommé `Data.xml`, le fichier doit ressembler à l’exemple de code suivant.  
  
   `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
4. Ajoutez l’attribut `type` à cet élément et lui fournir une valeur de `data`.  
  
   `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
5. Signer à nouveau votre manifeste d’application à l’aide de votre paire de clés ou un certificat et signer à nouveau votre manifeste de déploiement.  
  
    Vous devez resigner votre manifeste de déploiement, car son hachage du manifeste d’application a changé.  
  
    `mage -s app manifest -cf cert_file -pwd password`
  
    `mage -u deployment manifest -appm app manifest`
  
    `mage -s deployment manifest -cf certfile -pwd password`
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Pour inclure un fichier de données à l’aide de MageUI.exe  
  
1.  Ajouter le fichier de données à votre répertoire de l’application avec le reste des fichiers de votre application.  
  
2.  En règle générale, le répertoire de votre application sera un répertoire étiqueté avec la version actuelle du déploiement, par exemple, v1.0.0.0.  
  
3.  Sur le **fichier** menu, cliquez sur **ouvrir** pour ouvrir votre manifeste d’application.  
  
4.  Sélectionnez le **fichiers** onglet.  
  
5.  Dans la zone de texte en haut de l’onglet, entrez le répertoire qui contient les fichiers de votre application, puis cliquez sur **Populate**.  
  
     Votre fichier de données s’affiche dans la grille.  
  
6.  Définir le **Type de fichier** valeur du fichier de données à **données**.  
  
7.  Enregistrez le manifeste d’application et signer à nouveau le fichier.  
  
     *MageUI.exe* vous invite à resigner le fichier.  
  
8.  Signer à nouveau votre manifeste de déploiement  
  
     Vous devez resigner votre manifeste de déploiement, car son hachage du manifeste d’application a changé.  
  
## <a name="see-also"></a>Voir aussi  
 [Accéder aux données locales et distantes dans les applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)