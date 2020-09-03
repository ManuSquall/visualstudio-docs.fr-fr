---
title: Guide pratique pour exclure des projets d’une build
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c30dd912378fd933d29bff1d8828f31de58f9afa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85284319"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Guide pratique pour exclure des projets d’une build

Vous pouvez générer une solution sans générer tous les projets qu'elle contient. Par exemple, vous pouvez exclure un projet qui interrompt la génération. Vous pouvez ensuite générer le projet, une fois les problèmes identifiés et résolus.

Vous pouvez exclure un projet en adoptant les approches suivantes :

- Suppression temporaire du projet de la configuration de solution active.

- Création d’une configuration de solution qui n’inclut pas le projet.

Pour plus d’informations, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md).

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Pour supprimer temporairement un projet de la configuration de solution active

1. Dans la barre de menus, choisissez **générer**  >  **Configuration Manager**.

2. Dans le tableau **Contextes des projets**, localisez le projet que vous souhaitez exclure de la génération.

3. Dans la colonne **Build** pour le projet, décochez la case.

4. Choisissez le bouton **Fermer**, puis régénérez la solution.

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Pour créer une configuration de solution qui exclut un projet

1. Dans la barre de menus, choisissez **générer**  >  **Configuration Manager**.

2. Dans la liste Configuration de la **solution active** , choisissez **\<New>** .

3. Dans la zone **Nom**, entrez un nom pour la configuration de solution.

4. Dans la liste **Copier les paramètres à partir de**, choisissez la configuration de solution sur laquelle vous souhaitez baser la nouvelle configuration (par exemple, **Déboguer**), puis choisissez le bouton **OK**.

5. Dans la boîte de dialogue **Gestionnaire de configurations**, décochez la case dans la colonne **Build** pour le projet que vous souhaitez exclure, puis choisissez le bouton **Fermer**.

6. Dans la barre d’outils **Standard**, vérifiez que la nouvelle configuration de solution est la configuration active dans la zone **Configurations de solutions**.

7. Dans la barre de menus, choisissez **générer générer**la  >  **solution**.

## <a name="skipped-projects"></a>Projets ignorés

Les projets peuvent être ignorés pendant la génération, car ils ne sont pas à jour ou parce qu’ils sont exclus de la configuration. Visual Studio utilise MSBuild pour générer vos projets. MSBuild génère uniquement une cible si la sortie est antérieure à l’entrée, comme déterminé par les horodateurs de fichier. Pour forcer une régénération, utilisez la **solution générer la génération**de la commande  >  **Rebuild Solution**.

Dans le volet de **génération** de la fenêtre **sortie** , Visual Studio signale le nombre de projets à jour, le nombre qui a été généré avec succès, le nombre qui a échoué et le nombre qui a été ignoré. Le nombre ignoré n’inclut pas les projets qui n’ont pas été générés, car ils étaient à jour. Lorsque les projets sont exclus de la configuration active, ils sont ignorés pendant la génération. Dans la sortie de la génération, vous voyez un message indiquant que le projet est ignoré :

```output
2>------ Skipped Build: Project: ConsoleApp2, Configuration: Debug x86 ------
2>Project not selected to build for this solution configuration
```

Pour déterminer la raison pour laquelle un projet a été ignoré, notez la configuration active ( `Debug x86` dans l’exemple précédent) et choisissez **générer**  >  **Configuration Manager**. Vous pouvez afficher ou modifier les projets ignorés pour chaque configuration, comme indiqué dans cet article.

## <a name="see-also"></a>Voir aussi

- [Présentation des configurations de build](../ide/understanding-build-configurations.md)
- [Comment : créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md)
- [Comment : générer plusieurs configurations simultanément](../ide/how-to-build-multiple-configurations-simultaneously.md)
