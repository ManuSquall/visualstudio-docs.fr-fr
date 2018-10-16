---
title: 'Erreur : la dépendance &#39;fichier&#39; dans le projet &#39;projet&#39; ne peut pas être copié dans le répertoire d’exécution, car elle serait en conflit avec une dépendance &#39;fichier&#39; | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.tasklisterror.copy_version_conflict
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: douge
ms.openlocfilehash: 0a8d6fe7440a39fc207d8d9a1b56bea06547e273
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49274298"
---
# <a name="error-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-conflict-with-dependency-39file39"></a>Erreur : la dépendance &#39;fichier&#39; dans le projet &#39;projet&#39; ne peut pas être copié dans le répertoire d’exécution, car elle serait en conflit avec une dépendance &#39;fichier&#39;
Il existe un conflit entre des références, car plusieurs dépendances distinctes qui portent le même nom de fichier sont copiées dans le répertoire bin pour permettre à l’application de s’exécuter. Le répertoire d’exécution ne peut pas résoudre le conflit dans la mesure où aucune des dépendances n’est une référence principale.  
  
 Cette erreur entraîne l’échec de la build.  
  
 Le fait de double-cliquer sur cet élément de la liste des tâches vous conduit au nœud de références du projet où le conflit se présente.  
  
 **Pour corriger cette erreur**  
  
-   Configurez l’un des assemblys en référence directe de votre projet. Cette approche présente toutefois un inconvénient potentiel, puisqu’il n’est pas garanti que l’assembly que vous choisissez fonctionne avec les assemblys qui nécessitent une autre version de l’assembly référencé.  
  
     \- ou -  
  
-   Vérifiez que les deux copies de l’assembly portent un nom fort et se trouvent dans le Global Assembly Cache. Ceci élimine le besoin de copier les assemblys dans le répertoire bin.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)   
 [Global Assembly Cache](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)   
 [Assemblys avec nom fort](http://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)   
 [Gestion des versions des assemblys](http://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903)   
 [Guide pratique pour créer et supprimer les dépendances d’un projet](../ide/how-to-create-and-remove-project-dependencies.md)