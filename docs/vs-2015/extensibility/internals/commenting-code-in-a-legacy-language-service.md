---
title: Commenter du code dans un service de langage hérité | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd1405456ca9a6ba00926c82bcc7959ea36d26c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160910"
---
# <a name="commenting-code-in-a-legacy-language-service"></a>Commentaire du code dans un service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Les langages de programmation fournissent généralement un moyen d’annoter ou de commenter le code. Un commentaire est une section de texte qui fournit des informations supplémentaires sur le code, mais qui est ignorée lors de la compilation ou de l’interprétation.  
  
 Les classes MPF (Managed package Framework) assurent la prise en charge des commentaires et suppriment les marques de commentaire du texte sélectionné.  
  
## <a name="comment-styles"></a>Styles de commentaires  
 Il existe deux styles généraux de commentaire :  
  
1. Commentaires de ligne, où le commentaire se trouve sur une seule ligne.  
  
2. Bloquez les commentaires, où le commentaire peut inclure plusieurs lignes.  
  
   Les commentaires de ligne comportent généralement un caractère de début (ou des caractères), tandis que les commentaires de bloc comportent des caractères de début et de fin. Par exemple, en C#, un commentaire de ligne commence par//, et un commentaire de bloc commence par/* et se termine par \* /.  
  
   Lorsque l’utilisateur sélectionne la **sélection de commentaire** de commande dans le menu **Edition**  ->  **avancé** , la commande est routée vers la <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> méthode sur la <xref:Microsoft.VisualStudio.Package.Source> classe. Lorsque l’utilisateur sélectionne la commande supprimer les **marques de commentaire**, la commande est routée vers la <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> méthode.  
  
## <a name="supporting-code-comments"></a>Commentaires sur le code de prise en charge  
 Vous pouvez faire en sorte que votre service de langage prenne en charge les commentaires de code au moyen du `EnableCommenting` paramètre nommé de <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Cela définit la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> propriété de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Pour plus d’informations sur la définition des fonctionnalités du langage servicce, consultez [inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
 Vous devez également substituer la <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> méthode pour retourner une <xref:Microsoft.VisualStudio.Package.CommentInfo> structure avec les caractères de commentaire pour votre langue. Les caractères de commentaire de ligne de style C# sont la valeur par défaut.  
  
### <a name="example"></a>Exemple  
 Voici un exemple d’implémentation de la <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> méthode.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override CommentInfo GetCommentFormat() {  
            CommentInfo info = new CommentInfo();  
            info.LineStart       = "//";  
            info.BlockStart      = "/*";  
            info.BlockEnd        = "*/";  
            info.UseLineComments = true;  
            return info;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités du service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md)   
 [Inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)
