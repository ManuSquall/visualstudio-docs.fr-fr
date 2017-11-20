---
title: "Description du modèle active (. Fichiers VSDir) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5bc2f4a50996ccca6a56632166121bf9784629bb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="template-directory-description-vsdir-files"></a>Description du modèle active (. Fichiers VSDir)
Un fichier de description de répertoire de modèle (.vsdir) est un fichier texte qui permet à l’environnement de développement intégré (IDE) pour afficher les dossiers, les fichiers .vsz de l’Assistant et les fichiers de modèle qui sont associés à votre projet dans les boîtes de dialogue. Le contenu inclut un enregistrement par le fichier ou dossier. Tous les fichiers .vsdir dans un emplacement référencé sont fusionnées, bien que .vsdir qu’un seul fichier est généralement fourni pour décrire plusieurs dossiers, les Assistants ou les fichiers de modèle.  
  
 Dossiers (dans les sous-répertoires), les fichiers qui sont référencés dans le fichier .vsdir et le fichier .vsdir lui-même se trouvent dans le même répertoire. Lorsque l’IDE exécute un Assistant ou affiche un dossier ou un fichier dans le **nouveau projet** ou **ajouter un nouvel élément** boîtes de dialogue, l’IDE examine le répertoire qui contient les fichiers exécutées pour déterminer si un fichier .vsdir est présent. Si un fichier .vsdir est trouvé, l’IDE lit pour déterminer s’il contient une entrée du fichier ou dossier exécuté ou affiché. Si une entrée est trouvée, l’IDE utilise les informations de l’exécution de l’Assistant ou d’affichage du contenu.  
  
 L’exemple de code suivant est à partir du fichier SourceFiles.vsdir dans le \<EnvSDK > clé de Registre \BscPrj\BscPrj\BscPrjProjectItems\Source_Files :  
  
```  
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127  
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124  
```  
  
 Dans ce cas, les deux enregistrements sont dans un seul fichier. Une nouvelle ligne (retour chariot) sépare chaque enregistrement. Chaque ligne représente un type de fichier différent. Un canal de communication (&#124;) sépare les champs dans chaque enregistrement. Un seul répertoire peut contenir plusieurs fichiers .vsdir qui ont des noms de fichiers différents, ou vous pouvez avoir un seul fichier .vsdir pour chaque type de fichier.  
  
## <a name="fields"></a>Champs  
 Le tableau suivant répertorie les champs spécifiés pour chaque enregistrement.  
  
|Champ|Description|  
|-----------|-----------------|  
|Nom de chemin d’accès relatif (RelPathName)|Le nom du fichier .vsz, modèle ou dossier, tel que HeaderFile.h ou MyWizard.vsz. Ce champ peut également être un nom utilisé pour représenter un dossier.|  
|{clsidPackage}|Le GUID du VSPackage qui permet l’accès à des chaînes localisées, telles que LocalizedName, Description, IconResourceId et SuggestedBaseName, dans les ressources de bibliothèque (DLL) de DLL satellites le VSPackage. IconResourceId s’applique si DLLPath n’est pas fourni. **Remarque :** ce champ est facultatif, sauf si un ou plusieurs des champs précédentes sont un identificateur de ressource. Ce champ est en général vide pour les fichiers .vsdir qui correspondent aux Assistants tiers qui ne localisez pas leur texte.|  
|LocalizedName|Le nom localisé de l’Assistant ou le fichier de modèle. Ce champ peut être une chaîne ou un identificateur de ressource sous la forme « #ResID ». Ce nom s’affiche dans le **ajouter un nouvel élément** boîte de dialogue. **Remarque :** si LocalizedName est un identificateur de ressource, {clsidPackage} est obligatoire.|  
|SortPriority|Entier qui représente la priorité relative de ce fichier de modèle ou l’Assistant. Par exemple, si cet élément a la valeur 1, cet élément est affiché en regard des autres éléments avec une valeur de 1 et avant tous les éléments avec une valeur de tri de 2 ou plus.<br /><br /> Priorité de tri est relatif les éléments dans le même répertoire. Il peut être plus d’un fichier .vsdir dans le même répertoire. Dans ce cas, les éléments de tous les *.* fichiers VSDir dans ce répertoire sont fusionnés. Éléments avec la même priorité sont répertoriés par ordre lexicographique pas la casse du nom affiché. Le `_wcsicmp` fonction est utilisée pour classer les éléments.<br /><br /> Éléments non décrits dans les fichiers .vsdir incluent un numéro de priorité supérieur au nombre de priorité la plus élevé répertorié dans les fichiers .vsdir. Le résultat est que ces éléments sont à la fin de la liste affichée, quelle que soit leur nom.|  
|Description|La description localisée de l’Assistant ou le fichier de modèle. Ce champ peut être une chaîne ou un identificateur de ressource sous la forme « #ResID ». Cette chaîne apparaît dans le **nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue lorsque l’élément est sélectionné.|  
|DLLPath ou {clsidPackage}|Utilisé pour charger une icône pour le fichier de modèle ou l’Assistant. Cette icône est chargée en tant que ressource en dehors d’un fichier .dll ou .exe en utilisant le IconResourceId. Ce fichier .dll ou .exe peut être identifié à l’aide d’un chemin d’accès complet ou à l’aide d’un GUID d’un VSPackage. L’implémentation de la DLL du VSPackage est utilisée pour charger l’icône (pas la DLL du satellite).|  
|IconResourceId|L’identificateur de ressource dans l’implémentation de la DLL ou VSPackage DLL qui détermine l’icône à afficher.|  
|Indicateurs (<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>)|Utilisé pour activer ou désactiver la **nom** et **emplacement** champs sur le **ajouter un nouvel élément** boîte de dialogue. La valeur de la **indicateurs** champ est l’équivalent décimal de la combinaison de bits indicateurs requis.<br /><br /> Lorsqu’un utilisateur sélectionne un élément sur le **nouveau** onglet, le projet détermine si le champ nom et le champ d’emplacement affichés lorsque le **ajouter un nouvel élément** boîte de dialogue s’affiche tout d’abord. Un élément, via un fichier .vsdir, peut contrôler uniquement si les champs sont activés et désactivés lorsque l’élément est sélectionné.|  
|SuggestedBaseName|Représente le nom par défaut pour le fichier, un modèle ou un Assistant. Ce champ est une chaîne ou un identificateur de ressource sous la forme « #ResID ». L’IDE utilise cette valeur pour fournir un nom par défaut pour l’élément. Cette valeur de base est ajoutée avec une valeur entière pour rendre le nom unique, tel que MyFile21.asp.<br /><br /> Dans la liste précédente, Description, DLLPath, IconResourceId, indicateurs et SuggestedBaseNumber s’appliquent uniquement aux fichiers de modèle et l’Assistant. Ces champs ne s’appliquent pas aux dossiers. Cela est illustré dans le code dans le fichier BscPrjProjectItems dans le \<EnvSDK > clé de Registre \BscPrj\BscPrj\BscPrjProjectItems. Ce fichier contient trois enregistrements (une pour chaque dossier) avec quatre champs pour chaque enregistrement : RelPathName, {clsidPackage}, LocalizedName et SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120`|  
  
 Lorsque vous créez un fichier de l’Assistant, vous devez également envisager les problèmes suivants.  
  
-   Tout champ non requis pour lequel il n’existe pas de données significatives doit contenir un zéro (0) comme espace réservé.  
  
-   Si aucun nom localisé n’est fourni, le nom de chemin d’accès relatif est utilisé dans le fichier de l’Assistant.  
  
-   DLLPath substitue clsidPackage pour l’emplacement de l’icône.  
  
-   Si aucune icône n’est définie, l’environnement IDE remplace l’icône par défaut pour un fichier qui a cette extension.  
  
-   Si aucun nom de base suggérée est fourni, 'Project' est utilisé.  
  
-   Si vous supprimez les fichiers .vsz, des dossiers ou fichiers de modèle, vous devez également supprimer leurs enregistrements associés à partir du fichier .vsdir.  
  
## <a name="see-also"></a>Voir aussi  
 [Assistants](../../extensibility/internals/wizards.md)   
 [Fichier Assistant (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)