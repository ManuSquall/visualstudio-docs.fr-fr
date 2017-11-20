---
title: "La chaîne de connexion contient des informations d’identification avec un mot de passe de texte en clair et n’utilise pas la sécurité intégrée | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: e9c03f6c864894d0dee9a0fade3137f1a7c50cda
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>La chaîne de connexion contient des informations d'identification comprenant un mot de passe en texte clair et n'utilise pas la sécurité intégrée
Voulez-vous enregistrer la chaîne de connexion dans le fichier DBML actuel et les fichiers de configuration de l'application avec ces informations confidentielles ?  Cliquez sur Non pour enregistrer la chaîne de connexion sans les informations confidentielles.  
  
 Lorsque vous travaillez avec des connexions de données qui incluent des informations confidentielles (mots de passe inclus dans la chaîne de connexion), vous pouvez enregistrer la chaîne de connexion dans le fichier DBML et le fichier de configuration de l'application du projet, avec ou sans les informations confidentielles.  
  
> [!WARNING]
>  Si vous affectez explicitement la **connexion** propriétés **paramètres de l’Application** propriété **False** ajoutera le mot de passe pour le fichier DBML.  
  
### <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>Pour enregistrer la chaîne de connexion avec les informations confidentielles dans les paramètres d'application du projet  
  
-   Cliquez sur **Oui**.  
  
     La chaîne de connexion est stockée en tant que paramètre d'application. La chaîne de connexion intègre les informations sensibles dans le texte brut. Le fichier DBML ne contient pas les informations sensibles.  
  
### <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>Pour enregistrer la chaîne de connexion sans les informations confidentielles dans les paramètres d'application du projet  
  
-   Cliquez sur **Non**.  
  
     La chaîne de connexion est stockée en tant que paramètre d'application, mais le mot de passe n'est pas inclus.  
  
## <a name="see-also"></a>Voir aussi
[Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL des outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)