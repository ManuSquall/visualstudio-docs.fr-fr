---
title: Saisie semi-automatique des membres dans un service de langage hérité | Microsoft Docs
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
ms.openlocfilehash: 93182d61b6ecf5bf22ea7117bf8ccfd17e2acd1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839726"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Saisie semi-automatique de membre dans un service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La saisie semi-automatique des membres IntelliSense est une info-bulle qui affiche la liste des membres possibles d’une étendue particulière, comme une classe, une structure, une énumération ou un espace de noms. Par exemple, en C#, si l’utilisateur tape « This » suivi d’un point, une liste de tous les membres de la classe ou de la structure au niveau de la portée actuelle est présentée dans une liste à partir de laquelle l’utilisateur peut sélectionner.  
  
 Managed package Framework (MPF) assure la prise en charge de l’info-bulle et de la gestion de la liste dans l’info-bulle. tout ce qui est nécessaire, c’est la coopération de l’analyseur pour fournir les données qui s’affichent dans la liste.  
  
 Les services de langage hérités sont implémentés dans le cadre d’un VSPackage, mais la meilleure façon d’implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus, consultez [extension de l’éditeur et des services de langage](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
> Nous vous recommandons de commencer à utiliser la nouvelle API Editor dès que possible. Cela améliore les performances de votre service de langage et vous permet de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## <a name="how-it-works"></a>Fonctionnement  
 Voici les deux façons dont une liste de membres est affichée à l’aide des classes MPF :  
  
- Positionnement du signe insertion sur un identificateur ou après un caractère de fin de membre et sélection des membres de la **liste** dans le menu **IntelliSense** .  
  
- Le <xref:Microsoft.VisualStudio.Package.IScanner> scanneur détecte un caractère de fin de membre et définit un déclencheur de jeton <xref:Microsoft.VisualStudio.Package.TokenTriggers> pour ce caractère.  
  
  Un caractère d’achèvement de membre indique qu’un membre d’une classe, d’une structure ou d’une énumération doit suivre. Par exemple, en C# ou Visual Basic le caractère de fin de membre est un `.` , alors que en C++ le caractère est un `.` ou un `->` . La valeur du déclencheur est définie lorsque le caractère sélectionné du membre est analysé.  
  
### <a name="the-intellisense-member-list-command"></a>Commande IntelliSense de la liste des membres  
 La <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> commande lance un appel à la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> méthode sur la <xref:Microsoft.VisualStudio.Package.Source> classe et la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> méthode appelle, à son tour, l' <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Analyseur de méthode avec la raison de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason> .  
  
 L’analyseur détermine le contexte de la position actuelle, ainsi que le jeton sous ou juste avant la position actuelle. Sur la base de ce jeton, une liste de déclarations est présentée. Par exemple, en C#, si vous placez le signe insertion sur un membre de classe et que vous sélectionnez membres de la **liste**, vous recevez une liste de tous les membres de la classe. Si vous placez le signe insertion après un point qui suit une variable objet, vous recevez une liste de tous les membres de la classe que l’objet représente. Notez que si le signe insertion est positionné sur un membre lorsque la liste des membres est affichée, la sélection d’un membre de la liste remplace le membre sur lequel figure le signe insertion par celui de la liste.  
  
### <a name="the-token-trigger"></a>Déclencheur de jeton  
 Le <xref:Microsoft.VisualStudio.Package.TokenTriggers> déclencheur lance un appel à la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> méthode sur la <xref:Microsoft.VisualStudio.Package.Source> classe et la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> méthode appelle, à son tour, l’analyseur avec la raison de l’analyse <xref:Microsoft.VisualStudio.Package.ParseReason> (si le déclencheur a également inclus l' <xref:Microsoft.VisualStudio.Package.TokenTriggers> indicateur, la raison de l’analyse est celle <xref:Microsoft.VisualStudio.Package.ParseReason> qui combine la sélection des membres et la mise en surbrillance des accolades).  
  
 L’analyseur détermine le contexte de la position actuelle, ainsi que ce qui a été tapé avant le caractère Select du membre. À partir de ces informations, l’analyseur crée une liste de tous les membres de l’étendue demandée. Cette liste de déclarations est stockée dans l' <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet retourné par la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode. Si des déclarations sont retournées, l’info-bulle de l’outil de saisie semi-automatique des membres s’affiche. L’info-bulle est gérée par une instance de la <xref:Microsoft.VisualStudio.Package.CompletionSet> classe.  
  
## <a name="enabling-support-for-member-completion"></a>Activation de la prise en charge de l’achèvement des membres  
 L' `CodeSense` entrée de registre doit être définie sur 1 pour prendre en charge toute opération IntelliSense. Cette entrée de Registre peut être définie à l’aide d’un paramètre nommé passé à l' <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attribut User associé au package de langue. Les classes du service de langage lisent la valeur de cette entrée de Registre à partir de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propriété de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
 Si votre scanneur retourne le déclencheur de jeton de <xref:Microsoft.VisualStudio.Package.TokenTriggers> et que votre analyseur retourne une liste de déclarations, la liste de saisie semi-automatique des membres s’affiche.  
  
## <a name="supporting-member-completion-in-the-scanner"></a>Prise en charge de la saisie semi-automatique des membres dans le scanner  
 Le scanneur doit être en mesure de détecter un caractère de fin de membre et de définir le déclencheur de jeton de <xref:Microsoft.VisualStudio.Package.TokenTriggers> lorsque ce caractère est analysé.  
  
### <a name="example"></a> Exemple  
 Voici un exemple simplifié de détection du caractère de fin de membre et de la définition de l' <xref:Microsoft.VisualStudio.Package.TokenTriggers> indicateur approprié. Cet exemple est fourni à titre d’illustration uniquement. Elle suppose que votre scanneur contient une méthode `GetNextToken` qui identifie et retourne des jetons à partir d’une ligne de texte. L’exemple de code définit simplement le déclencheur à chaque fois qu’il voit le type de caractère approprié.  
  
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
  
## <a name="supporting-member-completion-in-the-parser"></a>Prise en charge de la saisie semi-automatique des membres dans l’analyseur  
 Pour la saisie semi-automatique des membres, la <xref:Microsoft.VisualStudio.Package.Source> classe appelle la <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> méthode. Vous devez implémenter la liste dans une classe dérivée de la <xref:Microsoft.VisualStudio.Package.Declarations> classe. <xref:Microsoft.VisualStudio.Package.Declarations>Pour plus d’informations sur les méthodes que vous devez implémenter, consultez la classe.  
  
 L’analyseur est appelé avec <xref:Microsoft.VisualStudio.Package.ParseReason> ou <xref:Microsoft.VisualStudio.Package.ParseReason> lorsqu’un caractère SELECT de membre est tapé. L’emplacement donné dans l' <xref:Microsoft.VisualStudio.Package.ParseRequest> objet est immédiatement après le caractère Select du membre. L’analyseur doit collecter les noms de tous les membres qui peuvent apparaître dans une liste de membres à ce moment précis dans le code source. L’analyseur doit ensuite analyser la ligne active pour déterminer l’étendue que l’utilisateur souhaite associer au caractère Select du membre.  
  
 Cette portée est basée sur le type de l’identificateur avant le caractère Select du membre. Par exemple, en C#, étant donné la variable membre `languageService` qui a un type `LanguageService` , tapez **LanguageService.** produit une liste de tous les membres de la `LanguageService` classe. Également en C#, en tapant **this.** produit une liste de tous les membres de la classe dans la portée actuelle.  
  
### <a name="example"></a> Exemple  
 L’exemple suivant montre une façon de remplir une <xref:Microsoft.VisualStudio.Package.Declarations> liste. Ce code suppose que l’analyseur construit une déclaration et l’ajoute à la liste en appelant une `AddDeclaration` méthode sur la `TestAuthoringScope` classe.  
  
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
