---
title: Description de l’annuaire de modèle (. Vsdir) Fichiers (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16ba609d5b05d565a12b38bd19e9a777851ced5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704690"
---
# <a name="template-directory-description-vsdir-files"></a>Fichiers de description de répertoire de modèles (.Vsdir)
Un fichier de description d’annuaire de modèle (.vsdir) est un fichier texte qui permet à l’environnement intégré de développement (IDE) d’afficher des dossiers, des fichiers .vsz de magicien, et des fichiers de modèle qui sont associés à votre projet dans des boîtes de dialogue. Le contenu comprend un enregistrement par fichier ou dossier. Tous les fichiers .vsdir dans un emplacement référencé sont fusionnés, bien qu’un seul fichier .vsdir soit généralement fourni pour décrire plusieurs dossiers, assistants ou fichiers de modèle.

 Les dossiers (sous-directeurs), les fichiers référencés dans le fichier .vsdir et le fichier .vsdir lui-même sont tous situés dans le même répertoire. Lorsque l’IDE exécute un assistant ou affiche un dossier ou un fichier dans le **nouveau projet** ou ajoutez des boîtes de dialogue **Nouvel Élément,** l’IDE examine l’annuaire qui contient les fichiers exécutés pour déterminer si un fichier .vsdir est présent. Si un fichier .vsdir est trouvé, l’IDE le lit pour déterminer s’il contient une entrée pour le dossier ou le fichier exécuté ou affiché. Si une entrée est trouvée, l’IDE utilise les informations dans l’exécution de l’assistant ou l’affichage du contenu.

 L’exemple de code suivant est tiré du fichier \<SourceFiles.vsdir dans la clé de registre EnvSDK>-BscPrj-BscPrj-BscPrjProjectItems-Source_Files :

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 Dans ce cas, deux dossiers sont dans un fichier. Une nouvelle ligne (caractère de retour de chariot) sépare chaque enregistrement. Chaque ligne représente un type de fichier différent. Un personnage de pipe (&#124;) sépare les champs de chaque enregistrement. Un répertoire unique peut contenir plusieurs fichiers .vsdir qui ont des noms de fichiers différents, ou vous pouvez avoir un fichier .vsdir pour chaque type de fichier.

## <a name="fields"></a>Champs
 Le tableau suivant répertorie les champs spécifiés pour chaque enregistrement.

| Champ | Description |
| - | - |
| Nom relatif de chemin (RelPathName) | Le nom du dossier, du modèle ou du fichier .vsz, comme HeaderFile.h ou MyWizard.vsz. Ce champ peut également être un nom utilisé pour représenter un dossier. |
| 'clsidPackage' | Le GUID du VSPackage qui permet l’accès à des chaînes localisées, telles que LocalizedName, Description, IconResourceId et SuggestedBaseName, dans les ressources de la bibliothèque de liaisons dynamiques par satellite (DLL) de vsPackage. IconResourceId s’applique si DLLPath n’est pas fourni. **Note:**  Ce champ est facultatif à moins qu’un ou plusieurs des champs précédents ne soient un identifiant de ressource. Ce champ est généralement vide pour les fichiers .vsdir qui correspondent avec des assistants tiers qui ne localisent pas leur texte. |
| LocalizedName (en) | Le nom localisé du fichier ou de l’assistant modèle. Ce champ peut être une chaîne ou un identifiant de ressource du formulaire "#ResID". Ce nom est affiché dans la boîte de dialogue **Add New Item.** **Note:**  Si LocalizedName est un identifiant de ressource, il faut alors 'clsidPackage'. |
| SortPriorité | Un integer représentant la priorité relative de ce fichier de modèle ou de magicien. Par exemple, si cet article a une valeur de 1, alors cet article est affiché à côté d’autres éléments d’une valeur de 1 et en avance sur tous les éléments avec une valeur de type de 2 ou plus.<br /><br /> La priorité de tri est relative aux éléments dans le même répertoire. Il peut y avoir plus d’un fichier .vsdir dans le même répertoire. Dans ce cas, les éléments de tous <em>.</em> vsdir fichiers dans ce répertoire sont fusionnés. Les articles ayant la même priorité sont énumérés dans l’ordre lexicomographique insensible au cas du nom affiché. La `_wcsicmp` fonction est utilisée pour commander les articles.<br /><br /> Les éléments non décrits dans les fichiers .vsdir comprennent un numéro prioritaire supérieur au nombre prioritaire le plus élevé figurant dans les fichiers .vsdir. Le résultat est que ces éléments sont à la fin de la liste affichée quel que soit leur nom. |
| Description | La description localisée du fichier de modèle ou de l’assistant. Ce champ peut être une chaîne ou un identifiant de ressource du formulaire "#ResID". Cette chaîne apparaît dans la **boîte de** dialogue New Project ou Ajouter de nouveaux **éléments** lorsque l’élément est sélectionné. |
| DLLPath ou 'clsidPackage' | Utilisé pour charger une icône pour le fichier de modèle ou un assistant. L’icône est chargée comme une ressource à partir d’un fichier .dll ou .exe en utilisant l’IconResourceId. Ce fichier .dll ou .exe peut être identifié soit en utilisant un chemin complet ou en utilisant un GUID d’un VSPackage. La mise en œuvre DLL du VSPackage est utilisée pour charger l’icône (pas le satellite DLL). |
| IconResourceId | L’identifiant de ressource dans le DLL ou VSPackage implémentation DLL qui détermine l’icône à afficher. |
| Drapeaux<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>( ) | Utilisé pour désactiver ou activer les champs **de nom** et **de localisation** sur la boîte de dialogue Add **New Item.** La valeur du champ **Flags** est l’équivalent décimal de la combinaison de drapeaux bit requis.<br /><br /> Lorsqu’un utilisateur sélectionne un élément sur le **nouvel** onglet, le projet détermine si le champ nom et le champ de localisation sont affichés lorsque la boîte de dialogue **Add New Item** est affichée pour la première fois. Un élément, via un fichier .vsdir, ne peut contrôler que si les champs sont activés par rapport à désactivé lorsque l’élément est sélectionné. |
| BaseName suggéré | Représente le nom par défaut pour le fichier, l’assistant ou le modèle. Ce champ est soit une chaîne ou un identifiant de ressource du formulaire "#ResID". L’IDE utilise cette valeur pour fournir un nom par défaut pour l’article. Cette valeur de base est jointe à une valeur integer pour rendre le nom unique, comme MyFile21.asp.<br /><br /> Dans la liste précédente, Description, DLLPath, IconResourceId, Flags, et SuggestedBaseNumber s’appliquent uniquement aux fichiers de modèle et d’assistant. Ces champs ne s’appliquent pas aux dossiers. Ce fait est illustré dans le code du fichier BscPrjProjectItems dans le \<fichier EnvSDK>-BscPrj-BscPrj-BscPrj-BscPrjProjectItems. Ce fichier contient trois enregistrements (un pour chaque dossier) avec quatre champs pour chaque enregistrement : RelPathName, 'clsidPackage', LocalizedName et SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 Lorsque vous créez un fichier d’assistant, vous devez également considérer les questions suivantes.

- Tout domaine non requis pour lequel il n’existe pas de données significatives devrait contenir un 0 (zéro) en tant que propriétaire de place.

- Si aucun nom localisé n’est fourni, le nom relatif du chemin est utilisé dans le fichier des sorciers.

- DLLPath remplace clsidPackage pour l’emplacement de l’icône.

- Si aucune icône n’est définie, l’IDE remplace l’icône par défaut pour un fichier qui a cette extension.

- Si aucun nom de base suggéré n’est fourni, 'Projet' est utilisé.

- Si vous supprimez les fichiers.vsz, dossiers ou fichiers de modèle, vous devez également supprimer leurs enregistrements associés du fichier .vsdir.

## <a name="see-also"></a>Voir aussi
- [Assistants](../../extensibility/internals/wizards.md)
- [Fichier Assistant (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
