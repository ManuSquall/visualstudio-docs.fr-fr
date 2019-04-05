---
title: Déterminer le Namespace par défaut d’un projet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- custom tools, computing default namespace
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 0bc5cba2651f447e36491c641e9b0d05f728e5c7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952531"
---
# <a name="determining-the-default-namespace-of-a-project"></a>Détermination de l’espace de noms par défaut d’un projet
Pour [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], si le `CustomToolNamespace` propriété est définie sur le fichier d’entrée, puis la valeur de `CustomToolNamespace` devient la valeur du paramètre d’espace de noms par défaut passé à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> (méthode). Sinon, le `wszDefaultNamespace` paramètre passé à `Generate` est toujours égal à l’espace de noms racine. Pour plus d’informations sur les espaces de noms, consultez [mots clés Namespace](http://msdn.microsoft.com/library/091a66eb-b10d-4f54-9102-5ac0d4bdb84b).  
  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] utilise des espaces de noms basés sur le dossier. Autrement dit, l’espace de noms se compose de l’espace de noms racine, ainsi que les noms de tous les dossiers contenant l’outil personnalisé. Chaque nom de dossier est converti en un identificateur valide, et tous les noms de séparent les périodes. Par exemple, si le fichier d’entrée est FolderA\FolderB\FolderC\MyInput.txt, et l’espace de noms racine est CL9, l’espace de noms par défaut calculée serait **CL9. FolderA.FolderB.FolderC**.  
  
 Une exception à cette règle se produit lorsque la chaîne de la hiérarchie contient un dossier de référence Web. Par exemple, si :  
  
- FolderC ont été un dossier de référence Web, de l’espace de noms serait **CL9. FolderC**.  
  
- DossierB étaient un dossier de référence Web, de l’espace de noms serait **CL9. FolderB.FolderC**.  
  
  Autrement dit, l’espace de noms utilise le format suivant :  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation de générateurs de fichier unique](../extensibility/internals/implementing-single-file-generators.md)   
 [L’inscription de générateurs de fichier unique](../extensibility/internals/registering-single-file-generators.md)   
 [Exposition des types aux concepteurs visuels](../extensibility/internals/exposing-types-to-visual-designers.md)