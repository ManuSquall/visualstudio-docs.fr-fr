---
title: Achèvement de membre dans un Service de langage hérité | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0cc22190c9228d2e166be94ed0d5cc78105e2404
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134030"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Achèvement de membre dans un Service de langage hérité
La saisie semi-automatique IntelliSense membre est une info-bulle qui affiche une liste de membres possibles d’une étendue particulière comme une classe, une structure, une énumération ou une espace de noms. Par exemple, en c#, si l’utilisateur tape « this » suivi d’un point, une liste de tous les membres de la classe ou structure dans l’étendue actuelle est présentée dans une liste à partir de laquelle l’utilisateur peut sélectionner.  
  
 Managed package framework (MPF) fournit la prise en charge pour l’info-bulle et la gestion de la liste dans l’info-bulle ; tout ce qui est nécessaire est coopération à partir de l’analyseur pour fournir les données qui apparaissent dans la liste.  
  
 Les services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour plus d’informations, consultez [étendre l’éditeur et les Services de langage](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## <a name="how-it-works"></a>Son fonctionnement  
 Voici deux façons dans lequel une liste de membres est affichée à l’aide des classes MPF :  
  
-   Le point d’insertion de positionnement sur un identificateur ou après un caractère de terminaison membre et en sélectionnant **liste des membres** à partir de la **IntelliSense** menu.  
  
-   Le <xref:Microsoft.VisualStudio.Package.IScanner> analyseur détecte un caractère de terminaison membre et définit un déclencheur d’émission de jeton de <xref:Microsoft.VisualStudio.Package.TokenTriggers> pour ce caractère.  
  
 Un caractère de terminaison membre indique qu’un membre d’une classe, une structure ou une énumération consiste à suivre. Par exemple, en c# ou Visual Basic, le caractère de fin de membre est une `.`, tandis que dans C++ le caractère est un `.` ou `->`. La valeur de déclencheur est définie lorsque le caractère de sélection de membre est analysé.  
  
### <a name="the-intellisense-member-list-command"></a>La commande de la liste des membres IntelliSense  
 Le <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> commande lance un appel à la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.Source> classe et le <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> (méthode), à son tour, appelle le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Analyseur de méthode avec le motif de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
 L’analyseur détermine le contexte de la position actuelle, ainsi que le jeton sous ou immédiatement avant la position actuelle. En fonction de ce jeton, une liste de déclarations est présentée. Par exemple, en c#, si vous placez le point d’insertion sur un membre de classe, puis sélectionnez **liste des membres**, vous obtenez une liste de tous les membres de la classe. Si vous placez le signe insertion après une période qui suit une variable objet, vous obtenez une liste de tous les membres de la classe qui représente l’objet. Notez que si le point d’insertion est placé sur un membre lorsque la liste des membres est affichée, sélectionnez un membre dans la liste remplace le membre le signe insertion sur avec celle de la liste.  
  
### <a name="the-token-trigger"></a>Le déclencheur de jeton  
 Le <xref:Microsoft.VisualStudio.Package.TokenTriggers> déclencheur lance un appel à la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.Source> classe et le <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> (méthode), appelle à son tour, l’analyseur avec le motif de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason> (si le déclencheur de jeton est également inclus les <xref:Microsoft.VisualStudio.Package.TokenTriggers> indicateur, la raison de l’analyse est <xref:Microsoft.VisualStudio.Package.ParseReason> qui combine la sélection de membres et la mise en surbrillance des accolades).  
  
 L’analyseur détermine le contexte de l’actuelle positionner ainsi que ce qui a été tapé avant le membre sélectionner caractère. À partir de ces informations, l’analyseur crée une liste de tous les membres de l’étendue demandée. Cette liste de déclarations est stockée dans le <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet qui est retourné à partir de la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> (méthode). Si toutes les déclarations sont retournées, l’info-bulle Saisie semi-automatique de membre s’affiche. L’info-bulle est géré par une instance de la <xref:Microsoft.VisualStudio.Package.CompletionSet> classe.  
  
## <a name="enabling-support-for-member-completion"></a>L’activation de la prise en charge pour l’exécution de membre  
 Vous devez avoir le `CodeSense` entrée de Registre est définie sur 1 pour prendre en charge toute opération IntelliSense. Cette entrée de Registre peut être définie avec un paramètre nommé passé à la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attribut associé au package de langue de l’utilisateur. Les classes de service de langage de lire la valeur de cette entrée de Registre à partir de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propriété sur la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
 Si votre scanneur retourne le jeton déclencheur de <xref:Microsoft.VisualStudio.Package.TokenTriggers>, votre analyseur renvoie une liste de déclarations, puis la liste de saisie semi-automatique du membre s’affiche.  
  
## <a name="supporting-member-completion-in-the-scanner"></a>Prise en charge de la saisie semi-automatique des membres dans l’analyseur  
 Le moteur d’analyse doit être en mesure de détecter un caractère de terminaison de membres et définir le déclencheur d’émission de jeton de <xref:Microsoft.VisualStudio.Package.TokenTriggers> lorsque ce caractère est analysé.  
  
### <a name="example"></a>Exemple  
 Voici un exemple simplifié de détecter le caractère de fin de membre et de configuration approprié <xref:Microsoft.VisualStudio.Package.TokenTriggers> indicateur. Cet exemple est à titre d’illustration uniquement. Il suppose que votre scanneur contient une méthode `GetNextToken` qui identifie et retourne les jetons à partir d’une ligne de texte. L’exemple de code définit simplement le déclencheur lorsqu’il détecte le type de caractère correct.  
  
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
  
## <a name="supporting-member-completion-in-the-parser"></a>Prise en charge d’achèvement de membre dans l’analyseur  
 Fin de membre, le <xref:Microsoft.VisualStudio.Package.Source> classe appelle la <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> (méthode). Vous devez implémenter la liste dans une classe dérivée de la <xref:Microsoft.VisualStudio.Package.Declarations> classe. Consultez la <xref:Microsoft.VisualStudio.Package.Declarations> classe pour plus d’informations sur les méthodes que vous devez implémenter.  
  
 L’analyseur est appelée avec <xref:Microsoft.VisualStudio.Package.ParseReason> ou <xref:Microsoft.VisualStudio.Package.ParseReason> quand un caractère de sélection de membre est tapé. L’emplacement donné le <xref:Microsoft.VisualStudio.Package.ParseRequest> objet est immédiatement après le membre Sélectionnez caractère. L’analyseur doit collecter les noms de tous les membres qui peuvent apparaître dans une liste de membres à ce moment précis dans le code source. Puis, l’analyseur doit analyser la ligne actuelle pour déterminer la portée de que l’utilisateur veut associé au caractère de sélection de membre.  
  
 Cette étendue est basée sur le type de l’identificateur avant le membre sélectionner caractère. Par exemple, en c#, étant donné la variable membre `languageService` qui a un type de `LanguageService`, en tapant **languageService.** génère une liste de tous les membres de la `LanguageService` classe. Également dans c#, en tapant **cela.** génère une liste de tous les membres de la classe dans l’étendue actuelle.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre une façon de remplir un <xref:Microsoft.VisualStudio.Package.Declarations> liste. Ce code suppose que l’analyseur construit une déclaration et l’ajoute à la liste en appelant un `AddDeclaration` méthode sur la `TestAuthoringScope` classe.  
  
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