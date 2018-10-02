---
title: 'Avertissement : la dépendance &#39;fichier&#39; dans le projet &#39;projet&#39; ne peut pas être copié dans le répertoire d’exécution, car elle remplacerait la référence &#39;fichier. &#39; | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.tasklisterror.copy_version_warning
ms.assetid: 116819f3-a4d4-48b5-9e71-7c54660d38ef
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: douge
ms.openlocfilehash: 7ea168095d67bb71d7aea9a1139a6df1956d14fb
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "47590438"
---
# <a name="warning-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-overwrite-the-reference-39file39"></a>Avertissement : la dépendance &#39;fichier&#39; dans le projet &#39;projet&#39; ne peut pas être copié dans le répertoire d’exécution, car elle remplacerait la référence &#39;fichier.&#39;
Un conflit existe entre des dépendances ; plusieurs fichiers d’assembly distincts ayant le même nom doivent être copiés dans le répertoire bin pour permettre à l’application de s’exécuter. Le répertoire d’exécution peut résoudre le conflit, car l’une des dépendances est une référence principale.  
  
 Le fait de double-cliquer sur cet élément de liste de tâche vous dirige vers le nœud de la référence principale en conflit.  
  
 Cet avertissement se produit quand vous êtes confronté à un conflit de dépendances, mais que vous l’avez éludé en ajoutant l’une des dépendances en conflit comme référence. Ou bien, vous aviez la version 1 d’une référence, puis en avez ajouté une deuxième qui fait elle-même référence à la version 2 de la première référence.  
  
 Autrement dit, cette erreur se produit parce que les projets de votre solution ont des références entre eux, mais les références ont été créées en tant que références de fichier (à l’aide de la **Parcourir** situé dans le [ajouter une référence](http://msdn.microsoft.com/en-us/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) boîte de dialogue zone), plutôt que des références entre projets (à l’aide de la **projet** onglet sur le **ajouter une référence** boîte de dialogue). L’avantage d’une référence de projet à projet est qu’elle crée une dépendance entre les projets dans le système de génération, si bien que le projet dépendant est généré s’il a été modifié depuis la dernière génération du projet de référence. Dans la mesure où une référence de fichier ne crée pas de dépendance de génération, il est possible de générer le projet de référence sans générer le projet dépendant, et une référence peut devenir obsolète ; un projet peut faire référence à une version précédemment générée du projet. De ce fait, plusieurs versions d’une même DLL peuvent être exigées dans le répertoire bin, ce qui n’est pas possible, et fait donc apparaître ce message d’erreur.  
  
 Ce message s’affiche chaque fois qu’il y a un conflit dans le répertoire bin et que l’application risque de ne pas fonctionner correctement. Même si vous avez contourné ce problème, cet avertissement continue de s’afficher, car le système de projet ne peut pas déterminer si la version d’une dépendance peut fonctionner correctement avec tous les composants.  
  
 **Pour corriger cette erreur**  
  
-   Copiez un (ou aucun) fichier d’assembly dans le répertoire bin, ce que vous pouvez faire en plaçant le fichier d’assembly dans le Global Assembly Cache. Le Global Assembly Cache résout les conflits de noms de fichiers. Aucune copie locale du fichier d’assembly n’est créée, car le common language runtime sait rechercher les assemblys dans le Global Assembly Cache. Pour plus d’informations, consultez [utilisation d’assemblys et le Global Assembly Cache](http://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433) et [erreur : Impossible de copier la dépendance 'fichier' du projet 'projet' dans le répertoire d’exécution, car elle serait en conflit avec la dépendance ' fichier '](../misc/error-the-dependency-file-in-project-project-cannot-be-copied-to-the-run-directory-because-it-would-conflict-with-dependency-file.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)   
 [Global Assembly Cache](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)   
 [Guide pratique pour créer et supprimer les dépendances d’un projet](../ide/how-to-create-and-remove-project-dependencies.md)