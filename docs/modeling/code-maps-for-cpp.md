---
title: Voir les dépendances entre les fichiers sources et d’en-tête C++
description: Fournit des informations sur les mappages de code pour les projets C++.
ms.date: 05/16/2018
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
ms.custom: SEO-VS-2020
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 93ac1f7364e23ef9ed2b44ecd1c536a7ab2b3d40
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389668"
---
# <a name="code-maps-for-c-projects"></a>Cartes de code pour les projets C++

Si vous souhaitez créer des cartes plus complètes pour des projets C++, définissez l’option du compilateur d’informations de consultation (**/FR**) sur ces projets. Sinon, un message vous invite à définir cette option. Si vous sélectionnez **OK**, l’option est définie uniquement pour la carte active. Vous pouvez choisir de masquer le message pour toutes les cartes ultérieures.

Lorsque vous ouvrez une solution qui contient des projets Visual C++, la mise à jour de la base de données IntelliSense peut prendre un certain temps. Pendant ce temps, vous ne pourrez peut-être pas créer de cartes de code pour les fichiers d’en-tête (*. h* ou `#include` ) tant que la base de données IntelliSense n’a pas terminé la mise à jour. Vous pouvez surveiller la progression des mises à jour dans la barre d’état de Visual Studio.

- Pour afficher les dépendances entre tous les fichiers sources et les fichiers d’en-tête de votre solution, sélectionnez **architecture**  >  **générer un graphique des fichiers include**.

   ![Graphique de dépendance pour le code natif](../modeling/media/dependencygraphgeneral_nativecode.png)

- Pour visualiser les dépendances entre le fichier actuellement ouvert et les fichiers sources et fichiers d’en-tête associés, ouvrez soit le fichier source, soit le fichier d’en-tête. Ouvrez le menu contextuel n’importe où dans le fichier. Choisissez **Générer le graphique des fichiers Include**.

   ![Graphique de dépendance de premier niveau pour le fichier .h](../modeling/media/dependencygraph_native_firstlevel.png)

## <a name="troubleshoot-code-maps-for-c-and-c-code"></a>Résoudre les problèmes liés aux cartes de code pour le code C et C++

Ces éléments ne sont pas pris en charge pour le code C et C++ :

- Les types de base n’apparaissent pas sur les cartes qui incluent la hiérarchie parente.

- La plupart des éléments de menu **Affichage** ne sont pas disponibles pour le code C et C++.

Ces problèmes peuvent se produire lorsque vous créez des cartes de code pour du code C et C++ :

|**Problème**|**Cause possible**|**Résolution :**|
|-|-|-|
|Échec de la génération de la carte de code.|Aucun projet de la solution n’a été généré correctement.|Corrigez les erreurs de build qui se sont produites, puis régénérez la carte.|
|Visual Studio cesse de répondre lorsque vous essayez de générer une carte de code à partir du menu **architecture** .|Le fichier de base de données du programme (.pdb) peut être endommagé.<br /><br /> Un fichier .pdb stocke des informations de débogage, telles que des informations sur le type, la méthode et le fichier source.|Régénérez la solution puis recommencez.|
|Certains paramètres de la base de données de navigation IntelliSense sont désactivés.|Certains paramètres IntelliSense peuvent être désactivés dans la boîte de dialogue **options** de Visual Studio.|Activez les paramètres.<br /><br /> Consultez [options, éditeur de texte, C/C++, avancé](../ide/reference/options-text-editor-c-cpp-advanced.md).|
|Le message **Méthodes inconnues** s’affiche sur un nœud de méthode.<br /><br /> Ce problème se produit car le nom de la méthode ne peut pas être résolu.|Le fichier binaire peut ne pas avoir de table de réadressage de base.|Activez l’option **/FIXED:NO** dans l’éditeur de liens.|
||Le fichier de base de données du programme (.pdb) peut ne pas être généré.<br /><br /> Un fichier .pdb stocke des informations de débogage, telles que des informations sur le type, la méthode et le fichier source.|Activez l’option **/DEBUG** dans l’éditeur de liens.|
||Impossible d’ouvrir ou de localiser le fichier .pdb aux emplacements attendus.|Assurez-vous que le fichier .pdb existe dans les emplacements attendus.|
||Les informations de débogage ont été supprimées du fichier .pdb.|Si l’option **/PDBSTRIPPED** a été utilisée dans l’éditeur de liens, incluez à la place le fichier .pdb complet.|
||L’appelant n’est pas une fonction ; il correspond à un thunk dans le fichier binaire ou à un pointeur dans la section de données.|Lorsque l’appelant est un thunk, essayez d’utiliser `_declspec(dllimport)` pour éviter le thunk.|

## <a name="see-also"></a>Voir aussi

- [Mapper des dépendances avec des cartes de code](../modeling/map-dependencies-across-your-solutions.md)
