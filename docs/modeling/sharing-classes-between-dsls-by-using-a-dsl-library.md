---
title: Partage de classes entre plusieurs DSL à l'aide d'une bibliothèque DSL
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38496141d6fcdd33f3bf5185c3f50b1bf961d832
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542543"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Partage de classes entre plusieurs DSL à l'aide d'une bibliothèque DSL
Dans le kit de développement logiciel (SDK) de visualisation et de modélisation Visual Studio, vous pouvez créer une définition DSL incomplète que vous pouvez importer dans un autre langage DSL. Cela vous permet de factoriser des parties courantes de modèles similaires.

## <a name="creating-and-using-dsl-libraries"></a>Création et utilisation de bibliothèques DSL

#### <a name="to-create-a-dsl-library"></a>Pour créer une bibliothèque DSL

1. Créez un projet DSL et choisissez le modèle de solution de bibliothèque DSL.

     Un projet DSL unique sera créé avec un modèle vide.

2. Vous pouvez ajouter des classes de domaine, des relations, des formes, etc.

     Les éléments de la bibliothèque n’ont pas besoin de former une seule arborescence d’incorporation.

     Pour définir une relation que les importateurs peuvent utiliser, créez deux classes de domaine et créez la relation entre elles.

     Envisagez de définir le **modificateur d’héritage** des classes de domaine sur `Abstract` .

3. Vous pouvez ajouter des éléments que vous définissez dans l’Explorateur DSL, tels que les générateurs de connexions.

4. Vous pouvez ajouter des personnalisations qui requièrent du code supplémentaire, telles que les contraintes de validation.

5. Cliquez sur **transformer tous les modèles**.

6. Créez le projet.

7. Lorsque vous distribuez le DSL pour d’autres personnes à utiliser, vous devez fournir à la fois l’assembly compilé (DLL) et le fichier `DslDefinition.dsl` . Vous pouvez trouver l’assembly compilé dans un dossier sous `Dsl\bin\*`

#### <a name="to-import-a-dsl-library"></a>Pour importer une bibliothèque DSL

1. Dans une autre définition DSL, dans l' **Explorateur DSL**, cliquez avec le bouton droit sur la classe racine du DSL, puis cliquez sur **Ajouter une nouvelle importation DslLibrary**.

2. Dans la Fenêtre Propriétés, définissez le **chemin d’accès** de la bibliothèque. Vous pouvez utiliser un chemin d’accès relatif ou absolu.

    La bibliothèque importée s’affiche dans l’Explorateur DSL, en mode lecture seule.

3. Vous pouvez utiliser les classes importées comme classes de base. Créez une classe de domaine dans le DSL d’importation et, dans le Fenêtre Propriétés, définissez **classe de base** sur une classe importée.

4. Cliquez sur Transformer tous les modèles.

5. Ajoutez au projet DSL une référence à l’assembly (DLL) qui a été généré par le projet de bibliothèque DSL.

6. Générez la solution.

   Une bibliothèque DSL peut importer d’autres bibliothèques. Lorsque vous importez une bibliothèque, ses importations s’affichent également automatiquement dans l’Explorateur DSL.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
