---
title: Prise en charge des extraits de Code dans un Service de langage hérité | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d0ca68c9d95f0b2b511ece0ecafbd9bdcacf328d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947428"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Prise en charge des extraits de code dans un service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un extrait de code est un morceau de code est inséré dans le fichier source. L’extrait de code est un modèle basé sur XML avec un ensemble de champs. Ces champs sont mis en surbrillance une fois que l’extrait de code est inséré et peut avoir des valeurs différentes en fonction du contexte dans lequel l’extrait de code est inséré. Immédiatement après que l’extrait de code est inséré, le service de langage peut mettre en forme l’extrait de code.  
  
 L’extrait de code est inséré dans un mode d’édition spéciale qui permet les champs de l’extrait de code pour permettre une navigation à l’aide de la touche TAB. Les champs peuvent prendre en charge les menus déroulants de type IntelliSense. L’utilisateur valide l’extrait de code dans le fichier source en tapant l’entrée ou la touche ÉCHAP. Pour en savoir plus sur les extraits de code, consultez [extraits de Code](../../ide/code-snippets.md).  
  
 Services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour plus d’informations, consultez [procédure pas à pas : Implémentation d’extraits de Code](../../extensibility/walkthrough-implementing-code-snippets.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## <a name="managed-package-framework-support-for-code-snippets"></a>Managed Package Framework prend en charge des extraits de Code  
 L’infrastructure de package managé (MPF) prend en charge la plupart des fonctionnalités de l’extrait de code, de lire le modèle à insérer l’extrait de code et permettant spéciale en mode édition. Prise en charge est gérée via la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe.  
  
 Lorsque le <xref:Microsoft.VisualStudio.Package.Source> classe est instanciée, la <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> méthode dans le <xref:Microsoft.VisualStudio.Package.LanguageService> classe est appelée pour obtenir un <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objet (Notez que la base de <xref:Microsoft.VisualStudio.Package.LanguageService> classe retourne toujours un nouveau <xref:Microsoft.VisualStudio.Package.ExpansionProvider> pour chaque objet <xref:Microsoft.VisualStudio.Package.Source> objet).  
  
 MPF ne prend pas en charge les fonctions d’extension. Une fonction d’expansion est une fonction nommée qui est incorporée dans un modèle d’extrait de code et retourne une ou plusieurs valeurs à placer dans un champ. Les valeurs sont retournées par le langage de service lui-même via un <xref:Microsoft.VisualStudio.Package.ExpansionFunction> objet. Le <xref:Microsoft.VisualStudio.Package.ExpansionFunction> objet doit être implémenté par le service de langage pour prendre en charge les fonctions d’extension.  
  
## <a name="providing-support-for-code-snippets"></a>Prise en charge pour les extraits de Code  
 Pour activer la prise en charge des extraits de code, vous devez fournir ou installer les extraits de code et vous devez fournir les moyens pour l’utilisateur d’insérer ces extraits de code. Il existe trois étapes de permettre la prise en charge des extraits de code :  
  
1.  Installation des fichiers d’extrait de code.  
  
2.  L’activation des extraits de code pour votre service de langage.  
  
3.  Appeler le <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objet.  
  
### <a name="installing-the-snippet-files"></a>Installation des fichiers d’extrait de code  
 Tous les extraits de code pour une langue sont stockés en tant que modèles dans des fichiers XML, généralement un modèle d’extrait par fichier. Pour plus d’informations sur le schéma XML utilisé pour les modèles d’extrait de code, consultez [référence de schéma des extraits de Code](../../ide/code-snippets-schema-reference.md). Chaque modèle d’extrait de code est identifié avec un ID de langue. Ce langage ID est spécifié dans le Registre et qu’il est placé dans le `Language` attribut de la \<Code > balise dans le modèle.  
  
 Il existe généralement deux emplacements où sont stockés les fichiers de modèle d’extrait de code : (1) où votre langage a été installé et 2) dans le dossier de l’utilisateur. Ces emplacements sont ajoutés au Registre ainsi que Visual Studio **Gestionnaire des extraits de Code** peut rechercher les extraits de code. Dossier de l’utilisateur est où les extraits de code créés par l’utilisateur sont stockés.  
  
 La mise en page de dossier par défaut pour les fichiers de modèle d’extrait de code installé ressemble à ceci : *[InstallRoot]*\\ *[TestLanguage]* \Snippets\\ *[LCID]* \Snippets.  
  
 *[InstallRoot]*  est le dossier d’installation dans votre langue.  
  
 *[TestLanguage]*  est le nom de votre langue comme nom de dossier.  
  
 *[LCID]*  est l’ID de paramètres régionaux. Voici comment les différentes versions de vos extraits sont stockés. Par exemple, l’ID de paramètres régionaux pour l’anglais est 1033, par conséquent, *[LCID]* est remplacé par 1033.  
  
 Un fichier supplémentaire doit être fourni et qui est un fichier d’index, généralement appelé SnippetsIndex.xml ou ExpansionsIndex.xml (vous pouvez utiliser n’importe quel nom de fichier valide se terminant par .xml). Ce fichier est généralement stocké dans le *[InstallRoot]*\\ *[TestLanguage]* dossier et spécifie l’emplacement exact du dossier des extraits de code, ainsi que l’ID de langue et le GUID du langage service qui utilise les extraits de code. Le chemin d’accès exact du fichier d’index est placé dans le Registre comme décrit plus loin dans « Installation les entrées de Registre ». Voici un exemple d’un fichier SnippetsIndex.xml :  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<SnippetCollection>  
    <Language Lang="Testlanguage" Guid="{b614a40a-80d9-4fac-a6ad-fc2868fff7cd}">  
        <SnippetDir>  
            <OnOff>On</OnOff>  
            <Installed>true</Installed>  
            <Locale>1033</Locale>  
            <DirPath>%InstallRoot%\TestLanguage\Snippets\%LCID%\Snippets\</DirPath>  
            <LocalizedName>Snippets</LocalizedName>  
        </SnippetDir>  
    </Language>  
</SnippetCollection>  
```  
  
 Le \<langue > balise spécifie l’ID de langue (le `Lang` attribut) et le service de langage GUID.  
  
 Cet exemple suppose que vous avez installé votre service de langage dans le dossier d’installation de Visual Studio. Le LCID % est remplacé par actuel ID de paramètres régionaux. l’utilisateur Plusieurs \<SnippetDir > balises peuvent être ajoutés, un pour chaque autre répertoire et les paramètres régionaux. En outre, un dossier d’extrait de code peut contenir des sous-dossiers, chacun d’eux est identifié dans le fichier d’index avec la \<SnippetSubDir > balise qui est incorporé dans un \<SnippetDir > balise.  
  
 Les utilisateurs peuvent également créer leurs propres extraits de code pour votre langage. Ceux-ci sont généralement stockés dans le dossier paramètres de l’utilisateur, par exemple *[TestDocs]* \Code extraits\\ *[TestLanguage]* \Test extraits de Code, où *[TestDocs]* est l’emplacement du dossier des paramètres de l’utilisateur pour Visual Studio.  
  
 Les éléments de substitution suivants peuvent être placés dans le chemin d’accès stocké dans le \<Chemin_du_répertoire > balise dans le fichier d’index.  
  
|Élément|Description|  
|-------------|-----------------|  
|%LCID%|ID de paramètres régionaux.|  
|%InstallRoot%|Dossier d’installation racine pour Visual Studio, par exemple, C:\Program Files\Microsoft Visual Studio 8.|  
|%ProjDir%|Dossier contenant le projet actuel.|  
|%ProjItem%|Dossier contenant l’élément de projet actuel.|  
|%TestDocs%|Dossier dans le dossier paramètres de l’utilisateur, par exemple, C:\Documents and Settings\\ *[username]* documents\Visual Studio\8.|  
  
### <a name="enabling-code-snippets-for-your-language-service"></a>L’activation des extraits de Code pour votre Service de langage  
 Vous pouvez activer des extraits de code pour votre service de langage en ajoutant le <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> attribut votre VSPackage (consultez [l’inscription d’un Service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md) pour plus d’informations). Le <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> et <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> paramètres sont facultatifs, mais vous devez inclure le `SearchPaths` paramètre nommé afin d’informer le **Gestionnaire des extraits de Code** de l’emplacement de vos extraits.  
  
 Voici un exemple montrant comment utiliser cet attribut :  
  
```  
[ProvideLanguageCodeExpansion(  
         typeof(TestSnippetLanguageService),  
         "Test Snippet Language",          // Name of language used as registry key  
         0,                               // Resource ID of localized name of language service  
         "Test Snippet Language",        // Name of Language attribute in snippet template  
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index  
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets  
```  
  
### <a name="calling-the-expansion-provider"></a>Appel du fournisseur d’extension  
 Le service de langage contrôle l’insertion de tout extrait de code, ainsi que la façon d’insertion est appelée.  
  
## <a name="calling-the-expansion-provider-for-code-snippets"></a>Appeler le fournisseur d’Expansion des extraits de Code  
 Il existe deux façons d’appeler le fournisseur d’expansion : à l’aide d’une commande de menu ou à l’aide d’un raccourci à partir d’une liste de saisie semi-automatique.  
  
### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Insérer un extrait de Code à l’aide d’une commande de Menu  
 Pour utiliser une commande de menu pour afficher le navigateur de l’extrait de code, vous ajoutez une commande de menu et appelez ensuite la <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> méthode dans le <xref:Microsoft.VisualStudio.Package.ExpansionProvider> interface en réponse à cette commande de menu.  
  
1.  Ajouter une commande et un bouton à votre fichier .vsct. Vous trouverez des instructions permettant d’effectuer dans [procédure pas à pas : Création d’une commande de Menu à l’aide du modèle de Package Visual Studio](http://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de).  
  
2.  Dérivez une classe de la <xref:Microsoft.VisualStudio.Package.ViewFilter> classe et substituer la <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> méthode pour indiquer la prise en charge de la nouvelle commande de menu. Cet exemple permet toujours de la commande de menu.  
  
    ```csharp  
    using Microsoft.VisualStudio.Package;  
  
    namespace TestLanguagePackage  
    {  
        class TestViewFilter : ViewFilter  
        {  
            public TestViewFilter(CodeWindowManager mgr, IVsTextView view)  
                : base(mgr, view)  
            {  
            }  
  
            protected override int QueryCommandStatus(ref Guid guidCmdGroup,  
                                                      uint nCmdId)  
            {  
                int hr = base.QueryCommandStatus(ref guidCmdGroup, nCmdId);  
                // If the base class did not recognize the command then  
                // see if we can handle the command.  
                if (hr == (int)Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP)  
                {  
                    if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)  
                    {  
                        if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)  
                        {  
                            hr = (int)(OLECMDF.OLECMDF_SUPPORTED | OLECMDF.OLECMDF_ENABLED);  
                        }  
                    }  
                }  
                return hr;  
            }  
        }  
    }  
    ```  
  
3.  Remplacer le <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> méthode dans le <xref:Microsoft.VisualStudio.Package.ViewFilter> classe pour obtenir le <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objet et appelez le <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> méthode sur cet objet.  
  
    ```csharp  
    using Microsoft.VisualStudio.Package;  
  
    namespace TestLanguagePackage  
    {  
        class TestViewFilter : ViewFilter  
        {  
            public override bool HandlePreExec(ref Guid guidCmdGroup,  
                                               uint nCmdId,  
                                               uint nCmdexecopt,  
                                               IntPtr pvaIn,  
                                               IntPtr pvaOut)  
            {  
                if (base.HandlePreExec(ref guidCmdGroup,  
                                       nCmdId,  
                                       nCmdexecopt,  
                                       pvaIn,  
                                       pvaOut))  
                {  
                    // Base class handled the command.  Do nothing more here.  
                    return true;  
                }  
  
                if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)  
                {  
                    if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)  
                    {  
                        ExpansionProvider ep = this.GetExpansionProvider();  
                        if (this.TextView != null && ep != null)  
                        {  
                            bool bDisplayed = ep.DisplayExpansionBrowser(  
                                this.TextView,  
                                "TestLanguagePackage Snippet:",  
                                null,  
                                false,  
                                null,  
                                false);  
                        }  
                        return true;   // Handled the command.  
                    }  
                }  
                return false;   // Did not handle the command.  
            }  
        }  
    }  
  
    ```  
  
     Les méthodes suivantes dans le <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe sont appelées par Visual Studio dans l’ordre indiqué au cours du processus de l’insertion de l’extrait de code :  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>  
  
5.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
6.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
7.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
8.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
     Après le <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> est appelée, l’extrait de code a été inséré et le <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objet est en mode édition spéciale utilisé pour la modification d’un extrait de code qui vient d’être inséré.  
  
### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Insérer un extrait de code à l’aide d’un raccourci  
 Implémentation d’un raccourci à partir d’une liste de saisie semi-automatique est beaucoup plus complexe que l’implémentation d’une commande de menu. Vous devez tout d’abord ajouter des raccourcis de l’extrait de code à la liste de saisie semi-automatique IntelliSense. Puis vous devez détecter quand un nom de raccourci d’extrait de code a été inséré à la suite de saisie semi-automatique. Enfin, vous devez obtenir le titre de l’extrait de code et le chemin d’accès en utilisant le nom de raccourci et transmettre ces informations pour le <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.ExpansionProvider> (méthode).  
  
 Pour ajouter des raccourcis de l’extrait de code à la liste de saisie semi-automatique, ajoutez-les à la <xref:Microsoft.VisualStudio.Package.Declarations> de l’objet dans votre <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe. Il se peut que vous devez vous assurer que vous pouvez identifier le raccourci comme un nom de l’extrait de code. Pour obtenir un exemple, consultez [Procédure pas à pas : Obtention d’une liste d’installé des extraits de Code (implémentation héritée)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
 Vous pouvez détecter l’insertion du raccourci d’extrait de code dans le <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> méthode de la <xref:Microsoft.VisualStudio.Package.Declarations> classe. Étant donné que le nom de l’extrait de code a déjà été inséré dans le fichier source, il doit être supprimé lors de l’expansion est insérée. Le <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> méthode prend une étendue qui décrit le point d’insertion pour l’extrait de code ; si l’étendue inclut le nom de l’extrait de code entier dans le fichier source, ce nom est remplacé par l’extrait de code.  
  
 Voici une version d’un <xref:Microsoft.VisualStudio.Package.Declarations> classe qui gère l’insertion d’extraits étant donné un nom de raccourci. Autres méthodes dans la <xref:Microsoft.VisualStudio.Package.Declarations> classe ont été omis par souci de clarté. Notez que le constructeur de cette classe prend un <xref:Microsoft.VisualStudio.Package.LanguageService> objet. Cela peut être passé à partir de votre version de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet (par exemple, votre implémentation de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe peut prendre la <xref:Microsoft.VisualStudio.Package.LanguageService> de l’objet dans son constructeur et passez cet objet à votre `TestDeclarations` constructeur de classe).  
  
```  
[C#]  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList       declarations;  
        private LanguageService languageService;  
        private TextSpan        commitSpan;  
  
        public TestDeclarations(LanguageService langService)  
            : base()  
        {  
            languageService = langService;  
            declarations = new ArrayList();  
        }  
  
        // This method is used to add declarations to the internal list.  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        // This method is called to get the string to commit to the source buffer.  
        // Note that the initial extent is only what the user has typed so far.  
        public override string OnCommit(IVsTextView textView,  
                                        string textSoFar,  
                                        char commitCharacter,  
                                        int index,  
                                        ref TextSpan initialExtent)  
        {  
            // We intercept this call only to get the initial extent  
            // of what was committed to the source buffer.  
            commitSpan = initialExtent;  
  
            return base.OnCommit(textView,  
                                 textSoFar,  
                                 commitCharacter,  
                                 index,  
                                 ref initialExtent);  
        }  
  
        // This method is called after the string has been committed to the source buffer.  
        public override char OnAutoComplete(IVsTextView textView,  
                                            string committedText,  
                                            char commitCharacter,  
                                            int index)  
        {  
            TestDeclaration item = declarations[index] as TestDeclaration;  
            if (item != null)  
            {  
                // In this example, TestDeclaration identifies types with a string.  
                // You can choose a different approach.  
                if (item.Type == "snippet")  
                {  
                    Source src = languageService.GetSource(textView);  
                    if (src != null)  
                    {  
                        ExpansionProvider ep = src.GetExpansionProvider();  
                        if (ep != null)  
                        {  
                            string title;  
                            string path;  
                            int commitLength = commitSpan.iEndIndex - commitSpan.iStartIndex;  
                            if (commitLength < committedText.Length)  
                            {  
                                // Replace everything that was inserted  
                                // so calculate the span of the full  
                                // insertion, taking into account what  
                                // was inserted when the commitSpan  
                                // was obtained in the first place.  
                                commitSpan.iEndIndex += (committedText.Length - commitLength);  
                            }  
  
                            if (ep.FindExpansionByShortcut(textView,  
                                                           committedText,  
                                                           commitSpan,  
                                                           true,  
                                                           out title,  
                                                           out path))  
                            {  
                                ep.InsertNamedExpansion(textView,  
                                                        title,  
                                                        path,  
                                                        commitSpan,  
                                                        false);  
                            }  
                        }  
                    }  
                }  
            }  
            return '\0';  
        }  
    }  
}  
```  
  
 Lorsque le service de langage Obtient le nom de raccourci, il appelle le <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> méthode pour obtenir le titre d’extrait de code de nom de fichier et le code. Le service de langage appelle ensuite la <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe pour insérer l’extrait de code. Les méthodes suivantes sont appelées par Visual Studio dans l’ordre indiqué dans la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe pendant le processus de l’insertion de l’extrait de code :  
  
1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
   Pour plus d’informations sur l’obtention d’une liste d’extraits de code installé pour votre service de langage, consultez [procédure pas à pas : Obtention d’une liste d’installé des extraits de Code (implémentation héritée)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
## <a name="implementing-the-expansionfunction-class"></a>Implémentation de la classe ExpansionFunction  
 Une fonction d’expansion est une fonction nommée qui est incorporée dans un modèle d’extrait de code et retourne une ou plusieurs valeurs à placer dans un champ. Pour prendre en charge les fonctions d’extension dans votre service de langage, vous devez dériver une classe à partir de la <xref:Microsoft.VisualStudio.Package.ExpansionFunction> classe et implémenter la <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> (méthode). Vous devez remplacer le <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> méthode dans le <xref:Microsoft.VisualStudio.Package.LanguageService> classe pour retourner une nouvelle instanciation de votre version de la <xref:Microsoft.VisualStudio.Package.ExpansionFunction> classe pour chaque fonction d’extension que vous prenez en charge. Si vous prenez en charge une liste de valeurs possibles à partir d’une fonction d’expansion, vous devez également substituer la <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.ExpansionFunction> classe pour retourner une liste de ces valeurs.  
  
 Une fonction d’expansion qui prend des arguments ou accéder aux autres champs ne doit pas être associée à un champ modifiable, car le fournisseur d’expansion ne peut pas être initialisé entièrement avant l’appel de la fonction d’expansion. Par conséquent, la fonction d’expansion n’est pas en mesure d’obtenir la valeur de ses arguments ou tout autre champ.  
  
### <a name="example"></a>Exemple  
 Voici un exemple de la façon dont une fonction d’expansion simple appelé `GetName` peut être implémenté. Cette fonction d’expansion ajoute un numéro à un nom de classe de base chaque fois que la fonction d’expansion est instanciée (qui correspond à chaque fois que l’extrait de code associé est inséré).  
  
```csharp  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private int classNameCounter = 0;  
  
        public override ExpansionFunction CreateExpansionFunction(  
            ExpansionProvider provider,  
            string functionName)  
        {  
            ExpansionFunction function = null;  
            if (functionName == "GetName")  
            {  
                ++classNameCounter;  
                function = new TestGetNameExpansionFunction(provider, classNameCounter);  
            }  
            return function;  
        }  
    }  
  
    internal class TestGetNameExpansionFunction : ExpansionFunction  
    {  
        private int nameCount;  
  
        TestGetNameExpansionFunction(ExpansionProvider provider, int counter)  
            : base(provider)  
        {  
            nameCount = counter;  
        }  
  
        public override string GetCurrentValue()  
        {  
            string name = "TestClass";  
            name += nameCount.ToString();  
            return name;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de Service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md)   
 [L’inscription d’un Service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Extraits de code](../../ide/code-snippets.md)   
 [Procédure pas à pas : Obtention d’une liste d’extraits de Code installés (implémentation héritée)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
