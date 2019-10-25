---
title: Considérations sur la sécurité du visualiseur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, security
- security [Visual Studio], visualizers
ms.assetid: cdd86bd5-b729-409b-a7c6-374efa091eb1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d53df0bc83e2068488c8a7c919f8b76258ad827
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728384"
---
# <a name="visualizer-security-considerations"></a>Considérations sur la sécurité du visualiseur
L'écriture d'un visualiseur implique d'éventuelles menaces pour la sécurité. Aucune attaque connue n'a été répertoriée concernant ces menaces potentielles, mais les développeurs doivent en être informés et prendre les précautions de sécurité appropriées, tel qu'indiqué ici, pour se protéger contre de futures attaques.

 Les visualiseurs de débogueur requièrent des privilèges plus importants que ceux octroyés par une application de confiance partielle. Les visualiseurs ne se chargent pas lorsque vous êtes arrêté dans du code à confiance partielle. Pour déboguer à l'aide d'un visualiseur, vous devez exécuter le code avec la confiance totale.

## <a name="possible-malicious-debuggee-component"></a>Composant d’élément débogué potentiellement malveillant
 Les visualiseurs sont composés d’au moins deux classes : une du côté débogueur et l’autre du côté de l’élément débogué. Les visualiseurs sont souvent déployés dans des assemblys séparés placés dans des répertoires spéciaux, mais ils peuvent également être chargés hors du programme débogué. Dans ce cas, le débogueur sort le code de l’élément débogué et l’exécute à l’intérieur du débogueur avec un niveau de confiance totale.

 L’exécution du code côté élément débogué avec la confiance totale devient problématique lorsque l’élément débogué n’est pas d’un niveau de confiance suffisant. Si un visualiseur essaie de charger un assembly de confiance partielle à partir du programme débogué dans le débogueur, Visual Studio arrête le visualiseur.

 Toutefois, il existe encore une vulnérabilité mineure. Le côté élément débogué peut s’associer à un côté débogueur qui a été chargé à partir d’une autre source (pas l’élément débogué). Le côté programme débogué peut alors indiquer au côté débogueur de confiance qu'il doit exécuter des actions de sa part. Si la classe côté débogueur de confiance expose un mécanisme "supprimer ce fichier", par exemple, l’élément débogué de confiance partielle pourrait appeler ce mécanisme lorsque l’utilisateur appelle son visualiseur.

 Afin d'atténuer cette vulnérabilité, faites attention aux interfaces exposées par votre visualiseur.

## <a name="see-also"></a>Voir aussi
- [Architecture d’un visualiseur](../debugger/visualizer-architecture.md)
- [Guide pratique pour écrire un visualiseur](/visualstudio/debugger/create-custom-visualizers-of-data)
- [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)
- [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)