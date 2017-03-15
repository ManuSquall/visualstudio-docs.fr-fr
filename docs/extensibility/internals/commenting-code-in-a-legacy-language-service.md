---
title: "Commentaires de Code dans un Service de langage h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "commentaires, prise en charge dans les services de langage (framework package managé)"
  - "services de langage (framework package managé), commentaires de code"
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Commentaires de Code dans un Service de langage h&#233;rit&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les langages de programmation fournissent généralement des méthodes pour annoter ou de commentaire du code.  Un commentaire est une section de texte qui fournit des informations supplémentaires à propos de le code mais est ignoré lors de la compilation ou la traduction.  
  
 Les classes managées du package \(MPF\) fournissent une prise en charge de commentaires et d'annuler les marques de commentaire du texte sélectionné.  
  
## styles de commentaire  
 Il existe deux styles généraux de commentaire :  
  
1.  La ligne commentaires, où est le commentaire sur une seule ligne.  
  
2.  Le bloc de commentaires, où le commentaire peut inclure plusieurs lignes.  
  
 Les commentaires de ligne ont en général un caractère de démarrage \(ou des caractères\), alors que les commentaires de bloc ont des caractères de début et de fin.  Par exemple, en c\#, démarrage d'un commentaire de ligne avec \/\/, et démarre un commentaire de bloc avec\/\* et se termine avec \*.  
  
 Lorsque l'utilisateur sélectionne la commande **sélection de commentaire** d' **Edit** \- le menu d'\> **Avancé** , la commande est routé vers la méthode d' <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> sur la classe d' <xref:Microsoft.VisualStudio.Package.Source> .  Lorsque l'utilisateur sélectionne la commande **Supprimez les marques de commentaire de la sélection**, la commande est routée vers la méthode d' <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> .  
  
## commentaires de code de prise en charge  
 Vous pouvez disposer commentaires du code de stockage après\-vente de langage via `EnableCommenting` nommé paramètre d' <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> .  Cela définit la propriété d' <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> de la classe d' <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .  Pour plus d'informations sur les fonctionnalités de servicce de langage de paramètre, consultez [L’inscription d’un Service de langage](../../extensibility/internals/registering-a-legacy-language-service1.md)\).  
  
 Vous devez également substituer la méthode d' <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> pour retourner une structure d' <xref:Microsoft.VisualStudio.Package.CommentInfo> avec les caractères de commentaire pour votre langage.  les caractères de style de la c\# de commentaire de la ligne est la valeur par défaut.  
  
### Exemple  
 voici un exemple d'implémentation de la méthode d' <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> .  
  
```c#  
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
  
## Voir aussi  
 [Fonctionnalités du Service de langage ancien](../../extensibility/internals/legacy-language-service-features1.md)   
 [L’inscription d’un Service de langage](../../extensibility/internals/registering-a-legacy-language-service1.md)