---
title: Description du répertoire de modèles (. Fichiers VSDir) | Microsoft Docs
description: Découvrez comment un fichier de description de répertoire de modèle permet à l’IDE de Visual Studio d’afficher des dossiers, des fichiers. vsz et des modèles associés à votre projet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bdd21dfa9fe5aae11553bb0268017690aba46fe9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080500"
---
# <a name="template-directory-description-vsdir-files"></a>Fichiers de description de répertoire de modèles (.Vsdir)
Un fichier de description de répertoire de modèles (. vsdir) est un fichier texte qui permet à l’environnement de développement intégré (IDE) d’afficher des dossiers, des fichiers Assistant. vsz et des fichiers modèles associés à votre projet dans des boîtes de dialogue. Le contenu inclut un enregistrement par fichier ou dossier. Tous les fichiers. vsdir d’un emplacement référencé sont fusionnés, bien qu’un seul fichier. vsdir soit généralement fourni pour décrire plusieurs dossiers, assistants ou fichiers de modèles.

 Les dossiers (sous-répertoires), les fichiers qui sont référencés dans le fichier. vsdir et le fichier. vsdir proprement dit se trouvent tous dans le même répertoire. Lorsque l’IDE exécute un Assistant ou affiche un dossier ou un fichier dans les boîtes de dialogue **nouveau projet** ou **Ajouter un nouvel élément** , l’IDE examine le répertoire qui contient les fichiers exécutés pour déterminer si un fichier. vsdir est présent. Si un fichier. vsdir est trouvé, l’IDE le lit pour déterminer s’il contient une entrée pour le dossier ou le fichier exécuté ou affiché. Si une entrée est trouvée, l’IDE utilise les informations dans l’exécution de l’Assistant ou l’affichage du contenu.

 L’exemple de code suivant provient du fichier SourceFiles. vsdir dans la \<EnvSDK> clé de Registre \bscprj\bscprj\bscprjprojectitems\ Source_Files :

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 Dans ce cas, deux enregistrements se trouvent dans un seul fichier. Une nouvelle ligne (retour chariot) sépare chaque enregistrement. Chaque ligne représente un type de fichier différent. Un caractère de barre verticale (&#124;) sépare les champs de chaque enregistrement. Un répertoire unique peut contenir plusieurs fichiers. vsdir qui ont des noms de fichiers différents, ou vous pouvez avoir un fichier. vsdir pour chaque type de fichier.

## <a name="fields"></a>Champs
 Le tableau suivant répertorie les champs spécifiés pour chaque enregistrement.

| Champ | Description |
| - | - |
| Nom de chemin d’accès relatif (RelPathName) | Nom du dossier, du modèle ou du fichier. vsz, tel que HeaderFile. h ou MyWizard. vsz. Ce champ peut également être un nom utilisé pour représenter un dossier. |
| {clsidPackage} | GUID du VSPackage qui permet d’accéder aux chaînes localisées, telles que LocalizedName, description, IconResourceId et SuggestedBaseName, dans les ressources de la bibliothèque de liens dynamiques (DLL) de satellite du VSPackage. IconResourceId s’applique si DLLPath n’est pas fourni. **Remarque :**  Ce champ est facultatif, sauf si un ou plusieurs des champs précédents sont un identificateur de ressource. Ce champ est généralement vide pour les fichiers. vsdir qui correspondent à des assistants tiers qui ne localisent pas leur texte. |
| LocalizedName | Nom localisé du fichier de modèle ou de l’Assistant. Ce champ peut être une chaîne ou un identificateur de ressource au format « #ResID ». Ce nom s’affiche dans la boîte de dialogue **Ajouter un nouvel élément** . **Remarque :**  Si LocalizedName est un identificateur de ressource, {clsidPackage} est requis. |
| SortPriority | Entier représentant la priorité relative de ce fichier de modèle ou de cet Assistant. Par exemple, si cet élément a la valeur 1, cet élément est affiché en regard des autres éléments avec la valeur 1 et avant tous les éléments dont la valeur de tri est supérieure ou supérieure à 2.<br /><br /> La priorité de tri est relative aux éléments dans le même répertoire. Il peut y avoir plusieurs fichiers. vsdir dans le même répertoire. Dans ce cas, les éléments de tous <em>.</em> les fichiers VSDir dans ce répertoire sont fusionnés. Les éléments de priorité identique sont répertoriés dans l’ordre de lexicographique ne respectant pas la casse du nom affiché. La `_wcsicmp` fonction est utilisée pour trier les éléments.<br /><br /> Les éléments non décrits dans les fichiers. vsdir incluent un numéro de priorité supérieur au numéro de priorité le plus élevé répertorié dans les fichiers. vsdir. Le résultat est que ces éléments se trouvent à la fin de la liste affichée, quel que soit leur nom. |
| Description | Description localisée du fichier de modèle ou de l’Assistant. Ce champ peut être une chaîne ou un identificateur de ressource au format « #ResID ». Cette chaîne apparaît dans la boîte de dialogue **nouveau projet** ou **Ajouter un nouvel élément** lorsque l’élément est sélectionné. |
| DLLPath ou {clsidPackage} | Utilisé pour charger une icône pour le fichier de modèle ou l’Assistant. L’icône est chargée en tant que ressource à partir d’un fichier. dll ou. exe à l’aide de IconResourceId. Ce fichier. dll ou. exe peut être identifié soit à l’aide d’un chemin d’accès complet, soit à l’aide d’un GUID d’un VSPackage. La DLL d’implémentation du VSPackage est utilisée pour charger l’icône (et non la DLL satellite). |
| IconResourceId | Identificateur de ressource dans la dll d’implémentation du fichier DLL ou VSPackage qui détermine l’icône à afficher. |
| Flags ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS> ) | Utilisé pour désactiver ou activer les champs **nom** et **emplacement** dans la boîte de dialogue **Ajouter un nouvel élément** . La valeur du champ **Flags** est l’équivalent décimal de la combinaison des indicateurs binaires requis.<br /><br /> Lorsqu’un utilisateur sélectionne un élément dans l’onglet **nouveau** , le projet détermine si le champ nom et le champ emplacement sont affichés lorsque la boîte de dialogue **Ajouter un nouvel élément** s’affiche pour la première fois. Un élément, par le biais d’un fichier. vsdir, peut contrôler uniquement si les champs sont activés ou désactivés lorsque l’élément est sélectionné. |
| SuggestedBaseName | Représente le nom par défaut du fichier, de l’Assistant ou du modèle. Ce champ est une chaîne ou un identificateur de ressource au format « #ResID ». L’IDE utilise cette valeur pour fournir un nom par défaut pour l’élément. Cette valeur de base est ajoutée avec une valeur entière pour rendre le nom unique, par exemple MyFile21. asp.<br /><br /> Dans la liste précédente, description, DLLPath, IconResourceId, Flags et SuggestedBaseNumber s’appliquent uniquement aux fichiers de modèle et d’Assistant. Ces champs ne s’appliquent pas aux dossiers. Ce fait est illustré dans le code du fichier BscPrjProjectItems de la \<EnvSDK> clé de Registre \BscPrj\BscPrj\BscPrjProjectItems. Ce fichier contient trois enregistrements (un pour chaque dossier) avec quatre champs pour chaque enregistrement : RelPathName, {clsidPackage}, LocalizedName et SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 Lorsque vous créez un fichier d’Assistant, vous devez également prendre en compte les problèmes suivants.

- Tout champ non requis pour lequel il n’existe pas de données significatives doit contenir une valeur 0 (zéro) comme espace réservé.

- Si aucun nom localisé n’est fourni, le nom de chemin d’accès relatif est utilisé dans le fichier de l’Assistant.

- DLLPath remplace clsidPackage pour l’emplacement de l’icône.

- Si aucune icône n’est définie, l’IDE remplace l’icône par défaut pour un fichier qui a cette extension.

- Si aucun nom de base suggéré n’est fourni, 'projet’est utilisé.

- Si vous supprimez les fichiers. vsz, les dossiers ou les fichiers de modèle, vous devez également supprimer leurs enregistrements associés du fichier. vsdir.

## <a name="see-also"></a>Voir aussi
- [Assistants](../../extensibility/internals/wizards.md)
- [Fichier Assistant (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
