---
title: "La cha&#238;ne de connexion contient des informations d&#39;identification avec un mot de passe en texte clair et n&#39;utilise pas la s&#233;curit&#233; int&#233;gr&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# La cha&#238;ne de connexion contient des informations d&#39;identification avec un mot de passe en texte clair et n&#39;utilise pas la s&#233;curit&#233; int&#233;gr&#233;e
Voulez\-vous enregistrer la chaîne de connexion dans le fichier DBML actuel et les fichiers de configuration de l'application avec ces informations confidentielles ?Cliquez sur Non pour enregistrer la chaîne de connexion sans les informations confidentielles.  
  
 Lorsque vous travaillez avec des connexions de données qui incluent des informations confidentielles \(mots de passe inclus dans la chaîne de connexion\), vous pouvez enregistrer la chaîne de connexion dans le fichier DBML et le fichier de configuration de l'application du projet, avec ou sans les informations confidentielles.  
  
> [!WARNING]
>  Si vous affectez explicitement à la propriété **Paramètres de l'application** des propriétés de **connexion** la valeur **False**, le mot de passe sera ajouté au fichier DBML.  
  
### Pour enregistrer la chaîne de connexion avec les informations confidentielles dans les paramètres d'application du projet  
  
-   Cliquez sur **Oui**.  
  
     La chaîne de connexion est stockée en tant que paramètre d'application.La chaîne de connexion intègre les informations sensibles dans le texte brut.Le fichier DBML ne contient pas les informations sensibles.  
  
### Pour enregistrer la chaîne de connexion sans les informations confidentielles dans les paramètres d'application du projet  
  
-   Cliquez sur **Non**.  
  
     La chaîne de connexion est stockée en tant que paramètre d'application, mais le mot de passe n'est pas inclus.  
  
## Voir aussi  
 [Concepteur Objet\/Relationnel \(Concepteur O\/R\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)