---
title: Détermination de l’espace de noms par défaut d’un projet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- custom tools, computing default namespace
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d58c8986922c30192d6300a623a635b24c34ed5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705773"
---
# <a name="determining-the-default-namespace-of-a-project"></a>Détermination de l’espace de noms par défaut d’un projet
Pour [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , si la `CustomToolNamespace` propriété est définie sur le fichier d’entrée, la valeur de `CustomToolNamespace` devient la valeur du paramètre d’espace de noms par défaut passé à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> méthode. Sinon, le `wszDefaultNamespace` paramètre passé à `Generate` est toujours égal à l’espace de noms racine. Pour plus d’informations sur les espaces de noms, consultez [Mots clés d’espace de noms](https://msdn.microsoft.com/library/091a66eb-b10d-4f54-9102-5ac0d4bdb84b).  
  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] utilise des espaces de noms basés sur des dossiers. Autrement dit, l’espace de noms se compose de l’espace de noms racine, ainsi que des noms de tous les dossiers contenant l’outil personnalisé. Chaque nom de dossier est converti en un identificateur valide et les périodes séparent tous les noms. Par exemple, si le fichier d’entrée est FolderA\FolderB\FolderC\MyInput.txt et que l’espace de noms racine est CL9, l’espace de noms calculé par défaut est **CL9. DossierA. FolderB. FolderC**.  
  
 Une exception à cette règle se produit lorsque la chaîne de hiérarchie contient un dossier de référence Web. Par exemple, si :  
  
- FolderC était un dossier de référence Web, l’espace de noms serait **CL9. FolderC**.  
  
- FolderB était un dossier de référence Web, l’espace de noms serait **CL9. FolderB. FolderC**.  
  
  Autrement dit, l’espace de noms utilise le format suivant :  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation de générateurs de fichier unique](../extensibility/internals/implementing-single-file-generators.md)   
 [Inscription de générateurs de fichier unique](../extensibility/internals/registering-single-file-generators.md)   
 [Exposition des types aux concepteurs visuels](../extensibility/internals/exposing-types-to-visual-designers.md)