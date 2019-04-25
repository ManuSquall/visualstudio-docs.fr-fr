---
title: Saisie semi-automatique de membres dans un Service de langage hérité | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a1fb236a4ce3b88f97dd94867b8ff5b7403db328
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950266"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Saisie semi-automatique de membre dans un service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La saisie semi-automatique de membres IntelliSense est une info-bulle qui affiche une liste de membres possibles d’une étendue particulière tel qu’une classe, structure, énumération ou espace de noms. Par exemple, en C#, si l’utilisateur tape « this » suivi d’un point, une liste de tous les membres de la classe ou structure dans la portée actuelle est présentée dans une liste à partir de laquelle l’utilisateur peut sélectionner.  
  
 L’infrastructure de package managé (MPF) fournit la prise en charge pour l’info-bulle et la gestion de la liste dans l’info-bulle ; tout ce qui est nécessaire est coopération à partir de l’analyseur pour fournir les données qui apparaissent dans la liste.  
  
 Services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour plus d’informations, consultez [extension de l’éditeur et les Services de langage](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## <a name="how-it-works"></a>Son fonctionnement  
 Voici les deux façons dans lequel une liste de membres est indiquée en utilisant les classes MPF :  
  
- Positionner le signe insertion sur un identificateur ou après un caractère de saisie semi-automatique de membre et en sélectionnant **liste des membres** à partir de la **IntelliSense** menu.  
  
- Le <xref:Microsoft.VisualStudio.Package.IScanner> scanneur détecte un caractère de saisie semi-automatique de membre et définit un déclencheur de jeton de <xref:Microsoft.VisualStudio.Package.TokenTriggers> pour ce caractère.  
  
  Un caractère de saisie semi-automatique de membre indique qu’un membre d’une classe, une structure ou une énumération consiste à suivre. Par exemple, en C# ou Visual Basic, le caractère de saisie semi-automatique de membre est un `.`, tandis que dans C++ le caractère est un `.` ou un `->`. La valeur du déclencheur est définie lorsque le caractère de sélection de membre est analysé.  
  
### <a name="the-intellisense-member-list-command"></a>La commande de liste de membres IntelliSense  
 Le <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> commande lance un appel à la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.Source> classe et le <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> (méthode), à son tour, appelle le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Analyseur de méthode avec le motif de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
 L’analyseur détermine le contexte de la position actuelle, ainsi que le jeton sous ou immédiatement avant la position actuelle. Une liste des déclarations en fonction de ce jeton, est présentée. Par exemple, en C#, si vous positionnez le point d’insertion sur un membre de classe, puis sélectionnez **liste des membres**, vous obtenez une liste de tous les membres de la classe. Si vous placez le signe insertion après une période qui suit une variable objet, vous obtenez une liste de tous les membres de la classe qui représente l’objet. Notez que si le signe insertion est positionné sur un membre lors de l’affichage de la liste des membres, vous sélectionnez un membre dans la liste remplace le membre le signe insertion sur avec celle de la liste.  
  
### <a name="the-token-trigger"></a>Le déclencheur de jeton  
 Le <xref:Microsoft.VisualStudio.Package.TokenTriggers> déclencheur lance un appel à la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.Source> classe et le <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> (méthode), appelle à son tour, l’analyseur avec le motif de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason> (si le déclencheur de jeton est également inclus la <xref:Microsoft.VisualStudio.Package.TokenTriggers> indicateur, la raison de l’analyse est <xref:Microsoft.VisualStudio.Package.ParseReason> qui combine la sélection de membre et la mise en surbrillance des accolades).  
  
 L’analyseur détermine le contexte du courant de position, ainsi que ce qui a été tapé avant le membre Sélectionnez caractère. À partir de ces informations, l’analyseur crée une liste de tous les membres de la portée demandée. Cette liste de déclarations est stockée dans le <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet qui est retourné à partir de la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> (méthode). Si toutes les déclarations sont retournées, l’info-bulle Saisie semi-automatique de membre s’affiche. L’info-bulle est géré par une instance de la <xref:Microsoft.VisualStudio.Package.CompletionSet> classe.  
  
## <a name="enabling-support-for-member-completion"></a>L’activation de la prise en charge pour la saisie semi-automatique de membres  
 Vous devez avoir le `CodeSense` entrée de Registre est définie sur 1 pour prendre en charge une opération IntelliSense. Cette entrée de Registre peut être définie avec un paramètre nommé transmis à la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> un attribut utilisateur associé au package de langage. Les classes de service de langage lire la valeur de cette entrée de Registre à partir de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propriété sur le <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
 Si le scanneur retourne le jeton déclencheur de <xref:Microsoft.VisualStudio.Package.TokenTriggers>, votre analyseur retourne une liste des déclarations, puis la liste de saisie semi-automatique de membre s’affiche.  
  
## <a name="supporting-member-completion-in-the-scanner"></a>Prise en charge de la saisie semi-automatique de membres dans l’analyseur  
 Le scanneur doit être en mesure de détecter un caractère de saisie semi-automatique de membre et définissez le déclencheur de jeton de <xref:Microsoft.VisualStudio.Package.TokenTriggers> lorsque ce caractère est analysé.  
  
### <a name="example"></a>Exemple  
 Voici un exemple simplifié de détecter le caractère de saisie semi-automatique de membre et de configuration approprié <xref:Microsoft.VisualStudio.Package.TokenTriggers> indicateur. Cet exemple est uniquement à des fins d’illustration. Il suppose que le scanneur contient une méthode `GetNextToken` qui identifie et retourne les jetons à partir d’une ligne de texte. L’exemple de code se contente de définir le déclencheur lorsqu’il détecte le type de caractère correct.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char memberSelectChar = '.';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (c == memberSelectChar)  
                {  
                        tokenInfo.Trigger |= TokenTriggers.MemberSelect;  
                }  
            }  
            return foundToken;  
        }  
    }  
}  
```  
  
## <a name="supporting-member-completion-in-the-parser"></a>Prise en charge de la saisie semi-automatique de membres dans l’analyseur  
 Pour la saisie semi-automatique de membres, le <xref:Microsoft.VisualStudio.Package.Source> classe appelle le <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> (méthode). Vous devez implémenter la liste dans une classe dérivée de la <xref:Microsoft.VisualStudio.Package.Declarations> classe. Consultez la <xref:Microsoft.VisualStudio.Package.Declarations> classe pour plus d’informations sur les méthodes que vous devez implémenter.  
  
 L’analyseur est appelé avec <xref:Microsoft.VisualStudio.Package.ParseReason> ou <xref:Microsoft.VisualStudio.Package.ParseReason> quand un caractère de sélection de membre est tapé. L’emplacement indiqué le <xref:Microsoft.VisualStudio.Package.ParseRequest> objet est immédiatement une fois que le membre sélectionné caractère. L’analyseur doit collecter les noms de tous les membres qui peuvent apparaître dans une liste des membres à ce moment précis dans le code source. Puis l’analyseur doit analyser la ligne actuelle pour déterminer la portée de que l’utilisateur veut associé avec le caractère de sélection de membre.  
  
 Cette étendue est basée sur le type de l’identificateur avant que le membre Sélectionnez caractère. Par exemple, en C#, étant donné la variable membre `languageService` qui a un type de `LanguageService`, en tapant **languageService.** génère une liste de tous les membres de la `LanguageService` classe. Également dans C#, en tapant **cela.** génère une liste de tous les membres de la classe dans la portée actuelle.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment remplir un <xref:Microsoft.VisualStudio.Package.Declarations> liste. Ce code part du principe que l’analyseur construit une déclaration et l’ajoute à la liste en appelant un `AddDeclaration` méthode sur le `TestAuthoringScope` classe.  
  
```csharp  
using System.Collections;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclaration  
    {  
        public string Name;            // Name of declaration  
        public int     TypeImageIndex; // Glyph index  
        public string Description;     // Description of declaration  
  
        public TestDeclaration(string name, int typeImageIndex, string description)  
        {  
            this.Name = name;  
            this.TypeImageIndex = typeImageIndex;  
            this.Description = description;  
        }  
    }  
  
    //===================================================  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList declarations;  
  
        public TestDeclarations()  
            : base()  
        {  
            declarations = new ArrayList();  
        }  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        //////////////////////////////////////////////////////////////////////  
        // Declarations of class methods that must be implemented.  
        public override int GetCount()  
        {  
            // Return the number of declarations to show.  
            return declarations.Count;  
        }  
  
        public override string GetDescription(int index)  
        {  
            // Return the description of the specified item.  
            string description = "";  
            if (index >= 0 && index < declarations.Count)  
            {  
                description = ((TestDeclaration)declarations[index]).Description;  
            }  
            return description;  
        }  
  
        public override string GetDisplayText(int index)  
        {  
            // Determine what is displayed in the tool tip list.  
            string text = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                text = ((TestDeclaration)declarations[index]).Name;  
            }  
            return text;  
        }  
  
        public override int GetGlyph(int index)  
        {  
            // Return index of image to display next to the display text.  
            int imageIndex = -1;  
            if (index >= 0 && index < declarations.Count)  
            {  
                imageIndex = ((TestDeclaration)declarations[index]).TypeImageIndex;  
            }  
            return imageIndex;  
        }  
  
        public override string GetName(int index)  
        {  
            string name = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                name = ((TestDeclaration)declarations[index]).Name;  
            }  
            return name;  
        }  
    }  
  
    //===================================================  
    public class TestAuthoringScope : AuthoringScope  
    {  
        private TestDeclarations declarationsList;  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            if (declaration != null)  
            {  
                if (declarationsList == null)  
                {  
                    declarationsList = new TestDeclarations();  
                }  
                declarationsList.AddDeclaration(declaration);  
            }  
        }  
  
        public override Declarations GetDeclarations(IVsTextView view,  
                                                     int line,  
                                                     int col,  
                                                     TokenInfo info,  
                                                     ParseReason reason)  
        {  
            return declarationsList;  
        }  
  
        /////////////////////////////////////////////////  
        // Remainder of AuthoringScope methods not shown.  
        /////////////////////////////////////////////////  
    }  
  
    //===================================================  
    class TestLanguageService : LanguageService  
    {  
        public override AuthoringScope ParseSource(ParseRequest req)  
        {  
            TestAuthoringScope scope = new TestAuthoringScope();  
            if (req.Reason == ParseReason.MemberSelect ||  
                req.Reason == ParseReason.MemberSelectAndHighlightBraces)  
            {  
                // Gather list of declarations based on what the user  
                // has typed so far. In this example, this list is an array of  
                // MemberDeclaration objects (a helper class you might implement  
                // to hold member declarations).  
                // How this list is gathered is dependent on the parser  
                // and is not shown here.  
                MemberDeclarations memberDeclarations;  
                memberDeclarations = GetDeclarationsForScope();  
  
                // Now populate the Declarations list in the authoring scope.  
                // GetImageIndexBasedOnType() is a helper method you  
                // might implement to convert a member type to an index into  
                // the image list returned from the language service.  
                foreach (MemberDeclaration dec in memberDeclarations)  
                {  
                    scope.AddDeclaration(new TestDeclaration(  
                                             dec.Name,  
                                             GetImageIndexBasedOnType(dec.Type),  
                                             dec.Description));  
                }  
            }  
            return scope;  
        }  
    }  
}  
```
