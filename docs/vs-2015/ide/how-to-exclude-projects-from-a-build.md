---
title: 'Procédure : Exclure des projets à partir d’une Build | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6a0b46a4aaa780357faa38a9ee4b01d04b1a0ba1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110925"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Procédure : Exclure des projets d’une build
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez générer une solution sans générer tous les projets qu'elle contient. Par exemple, vous pouvez exclure un projet qui interrompt la génération. Vous pouvez ensuite générer le projet, une fois les problèmes identifiés et résolus.  
  
 Vous pouvez exclure un projet en adoptant les approches suivantes :  
  
- Suppression temporaire du projet de la configuration de solution active.  
  
- Création d'une configuration de solution qui n'inclut pas le projet.  
  
  Pour plus d’informations, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md).  
  
### <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Pour supprimer temporairement un projet de la configuration de solution active  
  
1. Dans la barre de menus, choisissez **Générer**, puis **Gestionnaire de configurations**.  
  
2. Dans le tableau **Contextes des projets**, localisez le projet que vous souhaitez exclure de la génération.  
  
3. Dans la colonne **Build** pour le projet, décochez la case.  
  
4. Choisissez le bouton **Fermer**, puis régénérez la solution.  
  
### <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Pour créer une configuration de solution qui exclut un projet  
  
1. Dans la barre de menus, choisissez **Générer**, puis **Gestionnaire de configurations**.  
  
2. Dans la liste **Configuration de la solution active**, choisissez **\<Nouveau>**.  
  
3. Dans la zone **Nom**, entrez un nom pour la configuration de solution.  
  
4. Dans la liste **Copier les paramètres à partir de**, choisissez la configuration de solution sur laquelle vous souhaitez baser la nouvelle configuration (par exemple, **Déboguer**), puis choisissez le bouton **OK**.  
  
5. Dans la boîte de dialogue **Gestionnaire de configurations**, décochez la case dans la colonne **Build** pour le projet que vous souhaitez exclure, puis choisissez le bouton **Fermer**.  
  
6. Dans la barre d’outils **Standard**, vérifiez que la nouvelle configuration de solution est la configuration active dans la zone **Configurations de solutions**.  
  
7. Dans la barre de menus, choisissez **Générer**, **Régénérer la solution**.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des configurations de build](../ide/understanding-build-configurations.md)   
 [Guide pratique pour Créer et modifier des Configurations](../ide/how-to-create-and-edit-configurations.md)   
 [Guide pratique pour générer plusieurs configurations simultanément](../ide/how-to-build-multiple-configurations-simultaneously.md)
