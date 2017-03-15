---
title: "Bien démarrer avec PTVS : commencer à développer (projets) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14b85e70-b9a8-415c-a307-8c8c316a0495
caps.latest.revision: 6
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 96f7bc59b84e837b5a01eec0224171571491a7b1
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-ptvs-start-coding-projects"></a>Prise en main de PTVS : commencer à coder (projets)
Les outils Python pour Visual Studio (PTVS) vous permettent de gérer votre code. 
 
 Vous pouvez obtenir des instructions en regardant cette très courte [vidéo youtube](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2). 
 
 Si vous avez déjà utilisé Python, vous savez que votre projet est défini en fonction de la disposition des fichiers sur le disque. Cela fonctionne très bien pour les projets Python simples, mais pour plusieurs fichiers (pages web avec JavaScript, tests unitaires et scripts de compilation), les systèmes de fichiers peuvent être un peu limités. Visual Studio utilise les projets pour effectuer trois opérations. 
 
- Identifier les fichiers critiques. Les fichiers importants sont ceux que vous archivez dans un système de gestion de version (fichiers sources, ressources, etc.) et non les fichiers produits par la génération. Les fichiers importants sont aussi ceux que vous copiez sur un autre ordinateur pour permettre à une autre personne de travailler sur votre application. 
 
- Spécifier la façon dont les fichiers doivent être utilisés. Vous pouvez avoir des fichiers devant être traités par un outil chaque fois qu'ils sont modifiés. Les projets Visual Studio peuvent capturer ces informations 
 
- Définir les limites de vos composants. Si vous avez plusieurs composants dans votre application, vous pouvez les répartir dans des projets distincts. Ils peuvent éventuellement être déployés sur différents serveurs, créés avec différents paramètres de génération ou de débogage, ou même être écrits dans un autre langage pris en charge par Visual Studio, tel que C++ ou Node.js 
 
 Plusieurs modèles de projet sont à votre disposition pour vous aider à démarrer. Si vous voulez utiliser du code Python existant, l'Assistant À partir du code existant vous aide à créer un projet incluant tous vos fichiers. Il existe plusieurs projets web pour certaines infrastructures connues. D’autres modèles sont disponibles dans le pack d’exemples de PTVS. Certaines options permettent d'utiliser les modèles web fournis avec d'autres infrastructures. Le modèle Application Python est un projet propre et vide. Il existe un module pour vous aider à démarrer. 
 
 Visual Studio affiche vos projets ouverts dans la fenêtre de l'Explorateur de solutions, y compris tous les fichiers, chemins de recherche et environnements Python. Pour ajouter de nouveaux éléments, sélectionnez votre dossier de projet, choisissez Ajouter dans le menu contextuel (bouton droit du pointeur), puis Nouvel élément. Vous pouvez sélectionner n'importe quel élément de la boîte de dialogue, personnaliser le nom de l'élément et ajouter l'élément au projet. 
 
 Vous pouvez effectuer un glisser-déposer dans l'Explorateur de solutions. Si vous avez déjà copié les fichiers dans la structure de répertoire de votre projet, vous pouvez choisir Afficher tous les fichiers en haut de l'Explorateur de solutions. Vous pouvez ensuite sélectionner les éléments que vous voulez ajouter et choisir Inclure dans le projet dans le menu contextuel. 
 
 Vous pouvez obtenir des instructions en regardant cette très courte [vidéo youtube](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2). 
 
## <a name="see-also"></a>Voir aussi 
 [Documentation du wiki](https://github.com/Microsoft/PTVS/wiki/Projects) 
 [Vidéos sur le démarrage et l’exploration de PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
