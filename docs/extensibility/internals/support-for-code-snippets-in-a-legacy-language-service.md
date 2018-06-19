---
title: Prise en charge des extraits de Code dans un Service de langage hérité | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eb62481b9ba2c42ed067275480ba137b151a483b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135676"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Prise en charge des extraits de Code dans un Service de langage hérité
Un extrait de code est un fragment de code est inséré dans le fichier source. L’extrait de code est un modèle basé sur XML avec un ensemble de champs. Ces champs sont mis en surbrillance une fois l’extrait de code est inséré et peut avoir des valeurs différentes selon le contexte dans lequel l’extrait de code est inséré. Immédiatement après que l’extrait de code est inséré, le service de langage peut mettre en forme l’extrait de code.  
  
 L’extrait de code est inséré dans un mode d’édition spéciale qui permet les champs de l’extrait de code pour permettre une navigation à l’aide de la touche TAB. Les champs peuvent prendre en charge les menus déroulants de style IntelliSense. L’utilisateur est validée sur l’extrait de code au fichier source en tapant l’entrée ou sur la touche ÉCHAP. Pour en savoir plus sur les extraits de code, consultez [extraits de Code](../../ide/code-snippets.md).  
  
 Les services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour plus d’informations, consultez [procédure pas à pas : implémentation des extraits de Code](../../extensibility/walkthrough-implementing-code-snippets.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## <a name="managed-package-framework-support-for-code-snippets"></a>Managed Package Framework prend en charge des extraits de Code  
 Managed package framework (MPF) prend en charge la plupart des fonctionnalités de l’extrait de code, de lire le modèle à insérer l’extrait de code et permettant spéciales en mode édition. Prise en charge est gérée via la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe.  
  
 Lorsque le <xref:Microsoft.VisualStudio.Package.Source> classe est instanciée, la <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> méthode dans le <xref:Microsoft.VisualStudio.Package.LanguageService> classe est appelée pour obtenir un <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objet (Notez que la base de <xref:Microsoft.VisualStudio.Package.LanguageService> classe retourne toujours un nouveau <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objet pour chaque <xref:Microsoft.VisualStudio.Package.Source> objet).  
  
 MPF ne prend pas en charge les fonctions d’extension. Une fonction d’extension est une fonction nommée qui est incorporée dans un modèle extrait et renvoie une ou plusieurs valeurs à placer dans un champ. Les valeurs sont retournées par le langage service proprement dit via un <xref:Microsoft.VisualStudio.Package.ExpansionFunction> objet. Le <xref:Microsoft.VisualStudio.Package.ExpansionFunction> objet doit être implémenté par le service de langage pour prendre en charge les fonctions d’extension.  
  
## <a name="providing-support-for-code-snippets"></a>Prise en charge pour les extraits de Code  
 Pour activer la prise en charge des extraits de code, vous devez fournir ou installer les extraits de code et vous devez fournir les moyens de l’utilisateur d’insérer des extraits de code. Il existe trois étapes à activer la prise en charge des extraits de code :  
  
1.  Installation des fichiers d’extrait de code.  
  
2.  L’activation des extraits de code pour votre service de langage.  
  
3.  Appel de la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objet.  
  
### <a name="installing-the-snippet-files"></a>Installation des fichiers de l’extrait de code  
 Tous les extraits de code pour une langue sont stockés en tant que modèles dans des fichiers XML, en général un seul modèle extrait par fichier. Pour plus d’informations sur le schéma XML utilisé pour les modèles d’extrait de code, consultez [référence du schéma des extraits de Code](../../ide/code-snippets-schema-reference.md). Chaque modèle d’extrait de code est identifié avec un ID de langue. Ce langage ID est spécifié dans le Registre et qu’il est placé dans le `Language` attribut de le \<Code > balise dans le modèle.  
  
 Il existe généralement deux emplacements où sont stockés les fichiers de modèle d’extrait de code : (1) où votre langue a été installée et (2) dans le dossier de l’utilisateur. Ces emplacements sont ajoutés au Registre ainsi que Visual Studio **Gestionnaire des extraits de Code** peut rechercher les extraits de code. Dossier de l’utilisateur est où sont stockés les extraits de code créés par l’utilisateur.  
  
 La mise en page de dossier par défaut pour les fichiers de modèle d’extrait de code installé ressemble à ceci : *[InstallRoot]*\\ *[TestLanguage]* \Snippets\\ *[LCID]* \Snippets.  
  
 *[InstallRoot]*  est le dossier d’installation dans votre langue.  
  
 *[TestLanguage]*  est le nom de votre langue, comme un nom de dossier.  
  
 *[LCID]*  est l’ID de paramètres régionaux. Voici comment les différentes versions de vos extraits de code sont stockés. Par exemple, l’ID de paramètres régionaux pour l’anglais est 1033, par conséquent, *[LCID]* est remplacé par 1033.  
  
 Un fichier supplémentaire doit être fourni et qui est un fichier d’index, généralement appelé SnippetsIndex.xml ou ExpansionsIndex.xml (vous pouvez utiliser n’importe quel nom de fichier valide se terminant par .xml). Ce fichier est généralement stocké dans le *[InstallRoot]*\\ *[TestLanguage]* dossier et spécifie l’emplacement exact du dossier des extraits de code ainsi que l’ID de langue et le GUID de la langue service qui utilise les extraits de code. Le chemin d’accès exact du fichier d’index est placé dans le Registre comme décrit plus loin dans « Installation les entrées de Registre ». Voici un exemple d’un fichier SnippetsIndex.xml :  
  
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
  
 Le \<langue > balise spécifie l’ID de langue (le `Lang` attribut) et le GUID du service de langage.  
  
 Cet exemple suppose que vous avez installé votre service de langage dans le dossier d’installation de Visual Studio. Le LCID % est remplacé par actuel ID de paramètres régionaux. l’utilisateur Plusieurs \<SnippetDir > balises peuvent être ajoutés, une pour chaque autre répertoire et les paramètres régionaux. En outre, un dossier d’extrait de code peut contenir des sous-dossiers, chacun d’eux est identifié dans le fichier d’index avec la \<SnippetSubDir > balise qui est incorporé dans un \<SnippetDir > balise.  
  
 Ils peuvent également créer leurs propres extraits de code pour votre langue. Ceux-ci sont généralement stockés dans le dossier de paramètres de l’utilisateur, par exemple *[TestDocs]* \Code extraits\\ *[TestLanguage]* \Test extraits de Code, où *[TestDocs]* est l’emplacement du dossier des paramètres de l’utilisateur de Visual Studio.  
  
 Les éléments de substitution suivants peuvent être placés dans le chemin d’accès stocké dans le \<Chemin_du_répertoire > balise dans le fichier d’index.  
  
|Élément|Description|  
|-------------|-----------------|  
|LCID %|ID de paramètres régionaux.|  
|%InstallRoot%|Dossier d’installation racine pour Visual Studio, par exemple, C:\Program Files\Microsoft Visual Studio 8.|  
|% ProjDir %|Dossier contenant le projet actuel.|  
|% ProjItem %|Dossier contenant l’élément de projet actuel.|  
|% TestDocs %|Dossier dans le dossier des paramètres de l’utilisateur, par exemple, C:\Documents and Settings\\ *[username]* documents\Visual Studio\8.|  
  
### <a name="enabling-code-snippets-for-your-language-service"></a>L’activation des extraits de Code pour votre Service de langage  
 Vous pouvez activer des extraits de code pour votre service de langage en ajoutant la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> d’attributs pour votre VSPackage (consultez [l’inscription d’un Service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md) pour plus d’informations). Le <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> et <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> paramètres sont facultatifs, mais vous devez inclure le `SearchPaths` paramètre nommé afin d’informer le **Gestionnaire des extraits de Code** de l’emplacement de vos extraits de code.  
  
 Voici un exemple d’utilisation de cet attribut :  
  
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
 Le service de langage contrôle l’insertion d’un extrait de code, ainsi que la façon d’insertion est appelée.  
  
## <a name="calling-the-expansion-provider-for-code-snippets"></a>Appel du fournisseur d’extension pour les extraits de Code  
 Il existe deux façons d’appeler le fournisseur d’extension : à l’aide d’une commande de menu ou à l’aide d’un raccourci à partir d’une liste de saisie semi-automatique.  
  
### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Insérer un extrait de Code à l’aide d’une commande de Menu  
 Pour utiliser une commande de menu pour afficher le navigateur de l’extrait de code, vous ajoutez une commande de menu et appelez ensuite la <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> méthode dans le <xref:Microsoft.VisualStudio.Package.ExpansionProvider> interface en réponse à cette commande de menu.  
  
1.  Ajouter une commande et un bouton à votre fichier .vsct. Vous trouverez des instructions permettant d’effectuer dans [avec une commande de Menu pour créer une Extension](../../extensibility/creating-an-extension-with-a-menu-command.md).  
  
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
  
3.  Remplacer la <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> méthode dans le <xref:Microsoft.VisualStudio.Package.ViewFilter> classe pour obtenir le <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objet et appelez le <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> méthode sur cet objet.  
  
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
  
     Les méthodes suivantes dans le <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe sont appelés pendant le processus d’insertion de l’extrait de code par Visual Studio dans l’ordre indiqué :  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>  
  
5.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
6.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
7.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
8.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
     Après le <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> est appelée, l’extrait de code a été inséré et <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objet est en mode édition spéciale utilisé pour modifier un extrait de code qui vient d’être a été insérée.  
  
### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Insérer un extrait de code à l’aide d’un raccourci  
 Implémentation d’un raccourci à partir d’une liste de saisie semi-automatique est beaucoup plus compliquée que l’implémentation d’une commande de menu. Vous devez tout d’abord ajouter des raccourcis de l’extrait de code à la liste de saisie semi-automatique IntelliSense. Puis vous devez détecter lorsqu’un nom de raccourci d’extrait de code a été inséré à la suite d’achèvement. Enfin, vous devez obtenir le titre de l’extrait de code et le chemin d’accès à l’aide du nom raccourci et transmettre ces informations pour le <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.ExpansionProvider> (méthode).  
  
 Pour ajouter des raccourcis de l’extrait de code à la liste de saisie semi-automatique, ajoutez-les à la <xref:Microsoft.VisualStudio.Package.Declarations> de l’objet dans votre <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe. Il se peut que vous devez vous assurer que vous pouvez identifier le raccourci comme un nom de l’extrait de code. Pour obtenir un exemple, consultez [procédure pas à pas : obtention d’une liste d’installé des extraits de Code (implémentation hérité)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
 Vous pouvez détecter l’insertion du raccourci d’extrait de code dans le <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> méthode de la <xref:Microsoft.VisualStudio.Package.Declarations> classe. Étant donné que le nom de l’extrait de code a déjà été inséré dans le fichier source, il doit être supprimé lors de l’expansion est insérée. Le <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> méthode prend une étendue qui décrit le point d’insertion de l’extrait ; si l’étendue inclut le nom de l’extrait de code entier dans le fichier source, ce nom est remplacé par l’extrait de code.  
  
 Voici une version d’un <xref:Microsoft.VisualStudio.Package.Declarations> classe qui gère l’insertion d’extrait de code donnée un nom de raccourci. Autres méthodes dans la <xref:Microsoft.VisualStudio.Package.Declarations> classe ont été omis par souci de clarté. Notez que le constructeur de cette classe prend un <xref:Microsoft.VisualStudio.Package.LanguageService> objet. Cela peut être passé à partir de votre version de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet (par exemple, votre implémentation de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe peut prendre la <xref:Microsoft.VisualStudio.Package.LanguageService> de l’objet dans son constructeur et transmettre cet objet à votre `TestDeclarations` constructeur de classe).  
  
```csharp  
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
  
 Lorsque le service de langage Obtient le nom du raccourci, il appelle la <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> méthode pour obtenir le titre d’extrait de nom de fichier et le code. Le service de langage appelle ensuite la <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe pour insérer l’extrait de code. Les méthodes suivantes sont appelées par Visual Studio dans l’ordre indiqué dans la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe pendant le processus d’insertion de l’extrait de code :  
  
1.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
2.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
3.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
 Pour plus d’informations sur l’obtention d’une liste des extraits de code installé pour votre service de langage, consultez [procédure pas à pas : obtention d’une liste d’installé des extraits de Code (implémentation hérité)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
## <a name="implementing-the-expansionfunction-class"></a>Implémentation de la classe ExpansionFunction  
 Une fonction d’extension est une fonction nommée qui est incorporée dans un modèle extrait et renvoie une ou plusieurs valeurs à placer dans un champ. Pour prendre en charge les fonctions d’extension dans votre service de langage, vous devez dériver une classe à partir de la <xref:Microsoft.VisualStudio.Package.ExpansionFunction> classe et implémenter la <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> (méthode). Vous devez substituer la <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> méthode dans le <xref:Microsoft.VisualStudio.Package.LanguageService> classe pour retourner une nouvelle instanciation de votre version de la <xref:Microsoft.VisualStudio.Package.ExpansionFunction> classe pour chaque fonction d’extension que vous prenez en charge. Si vous prenez en charge une liste de valeurs possibles d’une fonction d’extension, vous devez également substituer la <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.ExpansionFunction> classe pour retourner une liste de ces valeurs.  
  
 Une fonction d’extension qui prend des arguments ou qui doit accéder aux autres champs ne doit pas être associée à un champ modifiable, car le fournisseur d’extension peut ne pas être entièrement initialisé au moment où que la fonction d’extension est appelée. Par conséquent, la fonction d’extension n’est pas en mesure d’obtenir la valeur de ses arguments ou tout autre champ.  
  
### <a name="example"></a>Exemple  
 Voici un exemple de la façon dont une fonction d’extension simple appelée `GetName` peut être implémenté. Cette fonction d’extension ajoute un nombre à un nom de classe de base chaque fois que la fonction d’extension est instanciée (qui correspond à chaque fois que l’extrait de code associé est inséré).  
  
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
 [Procédure pas à pas : Obtention d’une liste d’extraits de code installés (implémentation héritée)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)