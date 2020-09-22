---
title: Inclure un fichier de données dans une application ClickOnce
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: cdc2154876724feb5c6a0329a2acc5df7ac80fbc
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809144"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Guide pratique pour inclure un fichier de données dans une application ClickOnce
Chaque [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application que vous installez se voit attribuer un répertoire de données sur le disque local de l’ordinateur de destination, où l’application peut gérer ses propres données. Les fichiers de données peuvent inclure des fichiers de n’importe quel type : fichiers texte, fichiers XML ou même fichiers de base de données Microsoft Access (*. mdb*). Les procédures suivantes vous montrent comment ajouter un fichier de données de n’importe quel type dans votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application.

### <a name="to-include-a-data-file-by-using-mageexe"></a>Pour inclure un fichier de données à l’aide de Mage.exe

1. Ajoutez le fichier de données à votre répertoire d’application avec le reste des fichiers de votre application.

    En règle générale, le répertoire de votre application est un répertoire étiqueté avec la version actuelle du déploiement, par exemple, v 1.0.0.0.

2. Mettez à jour le manifeste de votre application pour répertorier le fichier de données.

    `mage -u v1.0.0.0\Application.manifest -FromDirectory v1.0.0.0`

    Cette tâche permet de recréer la liste des fichiers dans le manifeste de votre application et de générer automatiquement les signatures de hachage.

3. Ouvrez le manifeste de l’application dans votre éditeur de texte ou XML préféré et recherchez l' `file` élément correspondant à votre fichier récemment ajouté.

    Si vous avez ajouté un fichier XML nommé `Data.xml` , le fichier doit ressembler à l’exemple de code suivant.

   `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

4. Ajoutez l’attribut `type` à cet élément et fournissez-lui la valeur `data` .

   `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

5. Signez à nouveau votre manifeste d’application à l’aide de votre paire de clés ou certificat, puis resignez votre manifeste de déploiement.

    Vous devez signer à nouveau votre manifeste de déploiement, car son hachage du manifeste de l’application a changé.

    `mage -s app manifest -cf cert_file -pwd password`

    `mage -u deployment manifest -appm app manifest`

    `mage -s deployment manifest -cf certfile -pwd password`

### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Pour inclure un fichier de données à l’aide de MageUI.exe

1. Ajoutez le fichier de données à votre répertoire d’application avec le reste des fichiers de votre application.

2. En règle générale, le répertoire de votre application est un répertoire étiqueté avec la version actuelle du déploiement, par exemple, v 1.0.0.0.

3. Dans le menu **fichier** , cliquez sur **ouvrir** pour ouvrir le manifeste de votre application.

4. Sélectionnez l’onglet **fichiers** .

5. Dans la zone de texte en haut de l’onglet, entrez le répertoire qui contient les fichiers de votre application, puis cliquez sur **remplir**.

     Votre fichier de données s’affiche dans la grille.

6. Définissez la valeur de **type de fichier** du fichier de données sur **données**.

7. Enregistrez le manifeste de l’application, puis signez à nouveau le fichier.

     *MageUI.exe* vous invite à signer à nouveau le fichier.

8. Signer à nouveau votre manifeste de déploiement

     Vous devez signer à nouveau votre manifeste de déploiement, car son hachage du manifeste de l’application a changé.

## <a name="see-also"></a>Voir aussi
- [Accéder aux données locales et distantes dans les applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)