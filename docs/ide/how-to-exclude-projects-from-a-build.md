---
title: Guide pratique pour exclure des projets d’une build
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a19c49482c45aa0a3cf5d7cb33eb106adb65b83b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114804"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Guide pratique pour exclure des projets d’une build

Vous pouvez générer une solution sans générer tous les projets qu'elle contient. Par exemple, vous pouvez exclure un projet qui interrompt la génération. Vous pouvez ensuite générer le projet, une fois les problèmes identifiés et résolus.

Vous pouvez exclure un projet en adoptant les approches suivantes :

- Suppression temporaire du projet de la configuration de solution active.

- Création d’une configuration de solution qui n’inclut pas le projet.

Pour plus d’informations, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md).

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Pour supprimer temporairement un projet de la configuration de solution active

1. Sur la barre de menu, choisissez **Build** > **Configuration Manager**.

2. Dans le tableau **Contextes des projets**, localisez le projet que vous souhaitez exclure de la génération.

3. Dans la colonne **Build** pour le projet, décochez la case.

4. Choisissez le bouton **Fermer**, puis régénérez la solution.

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Pour créer une configuration de solution qui exclut un projet

1. Sur la barre de menu, choisissez **Build** > **Configuration Manager**.

2. Dans la liste **de configuration de solution Active,** choisissez ** \<New>**.

3. Dans la zone **Nom**, entrez un nom pour la configuration de solution.

4. Dans la liste **Copier les paramètres à partir de**, choisissez la configuration de solution sur laquelle vous souhaitez baser la nouvelle configuration (par exemple, **Déboguer**), puis choisissez le bouton **OK**.

5. Dans la boîte de dialogue **Gestionnaire de configurations**, décochez la case dans la colonne **Build** pour le projet que vous souhaitez exclure, puis choisissez le bouton **Fermer**.

6. Dans la barre d’outils **Standard**, vérifiez que la nouvelle configuration de solution est la configuration active dans la zone **Configurations de solutions**.

7. Sur la barre de menu, choisissez **Build** > **Rebuild Solution**.

## <a name="skipped-projects"></a>Projets ignorés

Les projets peuvent être ignorés pendant la construction parce qu’ils ne sont pas à jour ou parce qu’ils sont exclus de la configuration. Visual Studio utilise MSBuild pour construire vos projets. MSBuild ne construit une cible que si la sortie est plus ancienne que l’entrée, tel que déterminé par les délais de fichier. Pour forcer une reconstruction, utilisez la solution de reconstruction **de** > build**de**commande .

Dans le volet **Build** de la fenêtre **output,** Visual Studio rapporte le nombre de projets à jour, le nombre qui a construit avec succès, le nombre qui a échoué, et le nombre qui ont été ignorés. Le décompte ignoré n’inclut pas les projets qui n’ont pas été construits parce qu’ils étaient à jour. Lorsque les projets sont exclus de la configuration active, ils sont ignorés pendant la construction. Dans la sortie de la construction, vous voyez un message indiquant que le projet est ignoré :

```output
2>------ Skipped Build: Project: ConsoleApp2, Configuration: Debug x86 ------
2>Project not selected to build for this solution configuration
```

Pour savoir pourquoi un projet a été ignoré, notez la configuration active`Debug x86` (dans l’exemple précédent) et choisissez **Build** > Configuration**Manager**. Vous pouvez afficher ou modifier les projets qui sont ignorés pour chaque configuration, comme nous l’avons vu dans cet article.

## <a name="see-also"></a>Voir aussi

- [Présentation des configurations de build](../ide/understanding-build-configurations.md)
- [Comment : Créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md)
- [Comment : Construire plusieurs configurations simultanément](../ide/how-to-build-multiple-configurations-simultaneously.md)
