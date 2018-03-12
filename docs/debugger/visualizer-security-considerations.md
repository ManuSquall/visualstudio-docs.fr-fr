---
title: "Considérations sur la sécurité visualiseur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, security
- security [Visual Studio], visualizers
ms.assetid: cdd86bd5-b729-409b-a7c6-374efa091eb1
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d5075e55f1db35f7a588094a7c398c9d4c25483c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="visualizer-security-considerations"></a>Considérations sur la sécurité du visualiseur
L'écriture d'un visualiseur implique d'éventuelles menaces pour la sécurité. Aucune attaque connue n'a été répertoriée concernant ces menaces potentielles, mais les développeurs doivent en être informés et prendre les précautions de sécurité appropriées, tel qu'indiqué ici, pour se protéger contre de futures attaques.  
  
 Les visualiseurs de débogueur requièrent des privilèges plus importants que ceux octroyés par une application de confiance partielle. Les visualiseurs ne se chargent pas lorsque vous êtes arrêté dans du code à confiance partielle. Pour déboguer à l'aide d'un visualiseur, vous devez exécuter le code avec la confiance totale.  
  
## <a name="possible-malicious-debuggee-component"></a>Composant de programme débogué potentiellement malveillant  
 Les visualiseurs sont composés d'au moins deux classes : une du côté débogueur et l'autre du côté du programme débogué. Les visualiseurs sont souvent déployés dans des assemblys séparés placés dans des répertoires spéciaux, mais ils peuvent également être chargés hors de l’élément débogué. Dans ce cas, le débogueur sort le code du programme débogué et l'exécute à l'intérieur du débogueur avec un niveau de confiance totale.  
  
 L'exécution du code côté programme débogué avec la confiance totale devient problématique lorsque le programme débogué n'est pas d'un niveau de confiance suffisant. Si un visualiseur essaie de charger un assembly de confiance partielle à partir de l’élément débogué dans le débogueur, Visual Studio arrête le visualiseur.  
  
 Toutefois, il existe encore une vulnérabilité mineure. Le côté élément débogué peut s’associer à un côté débogueur qui a été chargé à partir d’une autre source (pas l’élément débogué). Le côté programme débogué peut alors indiquer au côté débogueur de confiance qu'il doit exécuter des actions de sa part. Si la classe côté débogueur de confiance expose un mécanisme "supprimer ce fichier", par exemple, l’élément débogué de confiance partielle pourrait appeler ce mécanisme lorsque l’utilisateur appelle son visualiseur.  
  
 Afin d'atténuer cette vulnérabilité, faites attention aux interfaces exposées par votre visualiseur.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture du visualiseur](../debugger/visualizer-architecture.md)   
 [Comment : écrire un visualiseur](../debugger/how-to-write-a-visualizer.md)   
 [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)   
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)