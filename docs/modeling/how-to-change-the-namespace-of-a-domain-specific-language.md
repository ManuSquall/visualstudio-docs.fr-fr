---
title: "Comment : modifier le Namespace d’un langage spécifique à un domaine | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, namespace
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fac213be46e86aab8767b71a8dff7dc10202321c
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Comment : modifier l'espace de nom d'un langage spécifique à un domaine
Vous pouvez modifier l’espace de noms d’un langage spécifique à un domaine. Vous devez apporter la modification dans le **Explorateur DSL**, dans les propriétés du projet de Package du Dsl et dans les informations d’assembly.  
  
### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Pour modifier l’espace de noms d’un langage spécifique à un domaine  
  
1.  Dans **Explorateur DSL**, cliquez sur le **Dsl** nœud.  
  
2.  Dans le **propriétés** fenêtre, de modifier le **Namespace** propriété.  
  
3.  Enregistrez la solution et transformer les modèles.  
  
4.  Sur le **projet** menu, cliquez sur **Dsl propriétés**.  
  
     Les propriétés de votre projet s’affichent.  
  
5.  Cliquez sur l’onglet **Application** .  
  
6.  Modifier la **par défaut d’espace de noms** propriété pour le nouveau nom de l’espace de noms.  
  
7.  Si vous souhaitez également modifier le nom de l’assembly, modifiez le **propriété Assembly name.**  
  
8.  Si vous avez modifié le nom de l’Assembly, ouvrez DslPackage\Package.tt et mettre à jour cette ligne :  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. Si vous avez écrit le code personnalisé, veillez à modifier l’espace de noms et les références dans les fichiers de code.  
  
10. Réinitialiser l’instance expérimentale de Visual Studio.  
  
    1.  Supprimer **\Users\\***{nom de votre}***\AppData\Local\Microsoft\VisualStudio\\\*Exp**  
  
    2.  Sur les fenêtres **Démarrer** menu, choisissez **tous les programmes**, **Microsoft Visual Studio 2010 SDK**, **outils**, **réinitialiser le Instance expérimentale**.  
  
11. Sur le **générer** menu, choisissez **régénérer la Solution**.  
  
## <a name="see-also"></a>Voir aussi

[Glossaire des outils de langage spécifique à un domaine](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)