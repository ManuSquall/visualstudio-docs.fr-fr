---
title: "Instructions de maintenance pour les Applications de Shell isol&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio Shell en mode intégré, facilité de maintenance"
  - "Interpréteur de commandes en mode intégré (Visual Studio), facilité de maintenance"
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Instructions de maintenance pour les Applications de Shell isol&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsque vous distribuez une application de shell isolé de Visual Studio, vous devez être en mesure de fournir des mises à jour logicielles pour votre application après son installation. Pour ce faire, vous devez installer votre application à l’aide d’un fichier Microsoft Installer \(MSI\). Ce type d’installation permet de mises à jour logicielles fournies par Microsoft pour être redistribué par le Web, téléchargement et consommée par vos clients sans intervention personnalisée.  
  
## Besoins en maintenance  
 Vous pouvez vous assurer que votre installation shell isolé peut autoriser des mises à jour en vous assurant que le programme d’installation répond à trois critères suivants.  
  
### Redistribution à l’aide d’un fichier MSI  
 Vous devez utiliser un fichier MSI pour redistribuer votre application, car un fichier MSI préserve l’identité du produit et permet de s’assurer que l’application a un emplacement physique sur l’ordinateur client. Les modules de fusion \(fichiers .msm\) ne fournissent pas ces garanties et ne doivent pas être utilisés.  
  
### Gestion des comptes pour les Actions personnalisées  
 Les actions personnalisées sont des directives d’installation non standard dans un programme d’installation. Actions personnalisées modifier des paramètres tels que les emplacements de fichiers, les paramètres de Registre, les paramètres utilisateur ou autres éléments de l’installation. Actions personnalisées peuvent manipuler des données au moment de l’installation.  
  
 Lorsque vous utilisez des actions personnalisées dans un programme d’installation, vous devez vous assurer que chaque action personnalisée au moment de l’installation doit avoir une action personnalisée correspondante pour annuler l’action lorsque l’utilisateur désinstalle l’application. Si votre programme d’installation échoue pour fournir correspondant désinstaller action personnalisée, suppression de votre application reste partiellement installé.  
  
-   Une action personnalisée qui s’appuie sur une version spécifique d’un fichier ou un hachage de valeurs échoue lors de la modification de ces versions de mises à jour ou valeurs de hachage. Dans ce cas l’action personnalisée doit mettre à jour manuellement ces valeurs. Un autre problème se produit si les versions d’un fichier ou un hachage de valeurs sont partagées entre les versions de produit. Évitez cette dépendance chaque fois que possible.  
  
### Gestion des comptes pour les fichiers partagés  
 Fichiers partagés ont le même nom et sont installés au même emplacement par plusieurs produits. Ces produits peuvent différer de la version, référence \(SKU Stock Keeping Unit\) ou les deux, et les produits peuvent coexister sur un ordinateur donné. Toutefois, les fichiers partagés créer des problèmes de maintenance pour plusieurs raisons :  
  
-   Mise à jour des fichiers partagés peut entraîner des problèmes de compatibilité des applications, car une mise à jour pour une application peut modifier la version d’un fichier utilisé par une autre application n’a pas été mis à jour. Programmes d’installation pour les produits qui partagent des fichiers nombre de références aux fichiers partagés. Par conséquent, la désinstallation d’un produit n’affecte pas les fichiers partagés au\-delà de décrémenter le nombre d’instances installées.  
  
-   Le programme d’installation de Quick Fix Engineering \(QFE\) rétablit les versions des fichiers pour les versions des produits par le programme d’installation du correctif QFE traitée. Ce processus compose potentiellement une application qui a fourni un fichier partagé mis à jour.