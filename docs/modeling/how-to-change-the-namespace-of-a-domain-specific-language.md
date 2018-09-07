---
title: "Comment : modifier l'espace de nom d'un langage spécifique à un domaine"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: a237664a30dacf351edc048c82d8c9cdc304aa45
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43775888"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Comment : modifier l'espace de nom d'un langage spécifique à un domaine
Vous pouvez modifier l’espace de noms d’un langage spécifique à un domaine. Vous devez apporter la modification dans le **Explorateur DSL**dans les propriétés du projet de Dsl Package et dans les informations de l’assembly.

### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Pour modifier l’espace de noms d’un langage spécifique à un domaine

1.  Dans **Explorateur DSL**, cliquez sur le **Dsl** nœud.

2.  Dans le **propriétés** fenêtre, de modifier le **Namespace** propriété.

3.  Enregistrez la solution et transformer les modèles.

4.  Sur le **projet** menu, cliquez sur **Dsl propriétés**.

     Les propriétés de votre projet s’affichent.

5.  Cliquez sur l’onglet **Application** .

6.  Modifier le **par défaut d’espace de noms** propriété vers le nouveau nom de l’espace de noms.

7.  Si vous souhaitez également modifier le nom de l’assembly, modifiez le **propriété Assembly name.**

8.  Si vous avez modifié le nom d’Assembly, ouvrez DslPackage\Package.tt et mettre à jour cette ligne :

     `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Si vous avez écrit n’importe quel code personnalisé, veillez à modifier les références d’espace de noms et classe dans les fichiers de code.

10. Réinitialiser l’instance expérimentale de Visual Studio.

    1.  Supprimer **\Users\\**_{nom de votre}_**\AppData\Local\Microsoft\VisualStudio\\\*Exp**

    2.  Sur le Windows **Démarrer** menu, choisissez **tous les programmes**, **Microsoft Visual Studio 2010 SDK**, **outils**, **réinitialiser le Instance expérimentale**.

11. Sur le **Build** menu, choisissez **régénérer la Solution**.

## <a name="see-also"></a>Voir aussi

- [Glossaire des outils Domain-Specific Language](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)