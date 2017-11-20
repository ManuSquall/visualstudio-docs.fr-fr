---
title: "Commentaires de Code dans un Service de langage hérité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8952612c9502704f79410461d29ca8ab87fa3ee4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="commenting-code-in-a-legacy-language-service"></a>Commentaires de Code dans un Service de langage hérité
En général, les langages de programmation fournissent un moyen d’annoter le code de commentaire. Un commentaire est une section de texte qui fournit des informations supplémentaires sur le code, mais est ignoré pendant la compilation ou une interprétation supplémentaire.  
  
 Les classes de framework (MPF) package managé prennent en charge les commentaire et de supprimer le commentaire de texte sélectionné.  
  
## <a name="comment-styles"></a>Styles de commentaire  
 Il existe deux styles générales de commentaire :  
  
1.  Commentaires sur une ligne où le commentaire se trouve sur une seule ligne.  
  
2.  Commentaires de bloc, où le commentaire peut inclure plusieurs lignes.  
  
 Commentaires sur une ligne ont généralement un caractère de début (ou caractères), lors de commentaires de bloc de caractères de début et de fin. Par exemple, en c#, un commentaire sur une ligne commence par / /, et commence par un bloc de commentaire / * et se termine par \*/.  
  
 Lorsque l’utilisateur sélectionne la commande **commenter la sélection** à partir de la **modifier** -> **avancé** menu, la commande est acheminée vers le <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.Source> classe. Lorsque l’utilisateur sélectionne la commande **ne pas commenter la sélection**, la commande est acheminée vers le <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> (méthode).  
  
## <a name="supporting-code-comments"></a>Prise en charge les commentaires de Code  
 Vous pouvez avoir vos commentaires de code langue service prise en charge par le biais de la `EnableCommenting` nommé de paramètre de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Cela permet de définir la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> propriété de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Pour plus d’informations sur la définition de langage servicce fonctionnalités, consultez [l’inscription d’un Service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
 Vous devez également substituer la <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> méthode pour retourner un <xref:Microsoft.VisualStudio.Package.CommentInfo> structure avec les caractères de commentaire pour votre langage. C#-caractères de commentaire de ligne de style sont la valeur par défaut.  
  
### <a name="example"></a>Exemple  
 Voici un exemple d’implémentation de la <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> (méthode).  
  
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
 [Fonctionnalités de Service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md)   
 [L’inscription d’un Service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)