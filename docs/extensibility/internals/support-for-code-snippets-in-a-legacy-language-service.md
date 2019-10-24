---
title: Prise en charge des extraits de code dans un service de langage hérité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d771db166baa66426c7a6d03b344c4bc7b74b27
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723108"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Prise en charge des extraits de code dans un service de langage hérité
Un extrait de code est un morceau de code qui est inséré dans le fichier source. L’extrait de code est un modèle XML avec un ensemble de champs. Ces champs sont mis en surbrillance après l’insertion de l’extrait de code et peuvent avoir des valeurs différentes en fonction du contexte dans lequel l’extrait de code est inséré. Immédiatement après l’insertion de l’extrait, le service de langage peut formater l’extrait de code.

 L’extrait de code est inséré dans un mode d’édition spécial qui permet de naviguer entre les champs de l’extrait à l’aide de la touche TAB. Les champs peuvent prendre en charge les menus déroulants de style IntelliSense. L’utilisateur valide l’extrait de code dans le fichier source en tapant la touche entrée ou ÉCHAP. Pour en savoir plus sur les extraits de code, consultez [extraits de code](../../ide/code-snippets.md).

 Les services de langage hérités sont implémentés dans le cadre d’un VSPackage, mais la meilleure façon d’implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus, consultez [procédure pas à pas : implémentation d’extraits de code](../../extensibility/walkthrough-implementing-code-snippets.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser la nouvelle API Editor dès que possible. Cela améliore les performances de votre service de langage et vous permet de tirer parti des nouvelles fonctionnalités de l’éditeur.

## <a name="managed-package-framework-support-for-code-snippets"></a>Prise en charge de l’infrastructure de package managée pour les extraits de code
 Managed package Framework (MPF) prend en charge la plupart des fonctionnalités d’extrait de code, de la lecture du modèle à l’insertion de l’extrait et de l’activation du mode d’édition spécial. La prise en charge est gérée via la classe <xref:Microsoft.VisualStudio.Package.ExpansionProvider>.

 Lorsque la classe <xref:Microsoft.VisualStudio.Package.Source> est instanciée, la méthode <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> de la classe <xref:Microsoft.VisualStudio.Package.LanguageService> est appelée pour obtenir un objet <xref:Microsoft.VisualStudio.Package.ExpansionProvider> (Notez que la classe <xref:Microsoft.VisualStudio.Package.LanguageService> de base retourne toujours un nouvel objet <xref:Microsoft.VisualStudio.Package.ExpansionProvider> pour chaque objet <xref:Microsoft.VisualStudio.Package.Source>).

 Le MPF ne prend pas en charge les fonctions d’expansion. Une fonction d’expansion est une fonction nommée qui est incorporée dans un modèle d’extrait de code et retourne une ou plusieurs valeurs à placer dans un champ. Les valeurs sont retournées par le service de langage lui-même via un objet <xref:Microsoft.VisualStudio.Package.ExpansionFunction>. L’objet <xref:Microsoft.VisualStudio.Package.ExpansionFunction> doit être implémenté par le service de langage pour prendre en charge les fonctions d’expansion.

## <a name="providing-support-for-code-snippets"></a>Prise en charge des extraits de code
 Pour activer la prise en charge des extraits de code, vous devez fournir ou installer les extraits de code et vous devez fournir les moyens permettant à l’utilisateur d’insérer ces extraits. Il existe trois étapes pour activer la prise en charge des extraits de code :

1. Installation des fichiers d’extraits de code.

2. Activation d’extraits de code pour votre service de langage.

3. Appel de l’objet <xref:Microsoft.VisualStudio.Package.ExpansionProvider>.

### <a name="installing-the-snippet-files"></a>Installation des fichiers d’extraits de code
 Tous les extraits de code d’une langue sont stockés sous forme de modèles dans des fichiers XML, généralement un modèle d’extrait par fichier. Pour plus d’informations sur le schéma XML utilisé pour les modèles d’extraits de code, consultez [référence de schéma des extraits de code](../../ide/code-snippets-schema-reference.md). Chaque modèle d’extrait de code est identifié par un ID de langue. Cet ID de langue est spécifié dans le registre et placé dans l’attribut `Language` de la balise > \<Code dans le modèle.

 Il existe généralement deux emplacements où les fichiers de modèle d’extrait de code sont stockés : 1) où votre langue a été installée et 2) dans le dossier de l’utilisateur. Ces emplacements sont ajoutés au registre afin que le **Gestionnaire des extraits de code** Visual Studio puisse trouver les extraits de code. Le dossier de l’utilisateur est l’emplacement de stockage des extraits de code créés par l’utilisateur.

 La disposition classique des fichiers du modèle d’extrait de code installé ressemble à ceci : *[InstallRoot]* \\ *[TestLanguage]* \Snippets \\ *[LCID]* \Snippets.

 *[InstallRoot]* est le dossier dans lequel votre langue est installée.

 *[TestLanguage]* est le nom de votre langue sous la forme d’un nom de dossier.

 *[LCID]* est l’ID de paramètres régionaux. Voici comment sont stockées les versions localisées de vos extraits de code. Par exemple, l’ID de paramètres régionaux pour l’anglais est 1033, donc *[LCID]* est remplacé par 1033.

 Un fichier supplémentaire doit être fourni et il s’agit d’un fichier d’index, généralement appelé SnippetsIndex. XML ou ExpansionsIndex. XML (vous pouvez utiliser n’importe quel nom de fichier valide se terminant par. Xml). Ce fichier est généralement stocké dans le dossier *[InstallRoot]* \\ *[TestLanguage]* et spécifie l’emplacement exact du dossier des extraits de code, ainsi que l’ID de langue et le GUID du service de langage qui utilise les extraits de code. Le chemin d’accès exact du fichier d’index est placé dans le registre, comme décrit plus loin dans la section « Installation des entrées du Registre ». Voici un exemple de fichier SnippetsIndex. xml :

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

 La balise \<Language > spécifie l’ID de langue (l’attribut `Lang`) et le GUID du service de langage.

 Cet exemple suppose que vous avez installé votre service de langage dans le dossier d’installation de Visual Studio. Le% LCID% est remplacé par l’ID de paramètres régionaux actuel de l’utilisateur. Vous pouvez ajouter plusieurs balises de > \<SnippetDir, une pour chaque répertoire et paramètres régionaux différents. En outre, un dossier d’extrait de code peut contenir des sous-dossiers, chacun d’entre eux étant identifié dans le fichier d’index avec la balise \<SnippetSubDir > qui est incorporée dans une balise de > \<SnippetDir.

 Les utilisateurs peuvent également créer leurs propres extraits de code pour votre langage. Celles-ci sont généralement stockées dans le dossier des paramètres de l’utilisateur, par exemple *[TestDocs]* \Code snippets \\ *[TestLanguage]* \test des extraits de code, où *[TestDocs]* est l’emplacement du dossier des paramètres de l’utilisateur pour Visual Studio.

 Les éléments de substitution suivants peuvent être placés dans le chemin d’accès stocké dans la balise \<DirPath > dans le fichier d’index.

|Élément|Description|
|-------------|-----------------|
|LCID|ID de paramètres régionaux.|
|InstallRoot|Dossier d’installation racine pour Visual Studio, par exemple, C:\Program Files\Microsoft Visual Studio 8.|
|%ProjDir%|Dossier contenant le projet actif.|
|%ProjItem%|Dossier contenant l’élément de projet actuel.|
|%TestDocs%|Dans le dossier des paramètres de l’utilisateur, par exemple, C:\Documents and Settings \\ *[username]* \Mes documents\Visual Studio\8.|

### <a name="enabling-code-snippets-for-your-language-service"></a>Activation d’extraits de code pour votre service de langage
 Vous pouvez activer les extraits de code pour votre service de langage en ajoutant l’attribut <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> à votre VSPackage (pour plus d’informations, consultez [inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md) ). Les paramètres <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> et <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> sont facultatifs, mais vous devez inclure le paramètre nommé `SearchPaths` afin d’informer le **Gestionnaire des extraits de code** de l’emplacement de vos extraits de code.

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

### <a name="calling-the-expansion-provider"></a>Appel du fournisseur de développement
 Le service de langage contrôle l’insertion de tout extrait de code, ainsi que la façon dont l’insertion est appelée.

## <a name="calling-the-expansion-provider-for-code-snippets"></a>Appel du fournisseur de développement pour les extraits de code
 Il existe deux façons d’appeler le fournisseur de développement : à l’aide d’une commande de menu ou à l’aide d’un raccourci d’une liste de saisie semi-automatique.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Insertion d’un extrait de code à l’aide d’une commande de menu
 Pour utiliser une commande de menu pour afficher l’Explorateur d’extraits, vous devez ajouter une commande de menu, puis appeler la méthode <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> dans l’interface <xref:Microsoft.VisualStudio.Package.ExpansionProvider> en réponse à cette commande de menu.

1. Ajoutez une commande et un bouton à votre fichier. vsct. Vous trouverez des instructions sur [la création d’une extension à l’aide d’une commande de menu](../../extensibility/creating-an-extension-with-a-menu-command.md).

2. Dérivez une classe de la classe <xref:Microsoft.VisualStudio.Package.ViewFilter> et substituez la méthode <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> pour indiquer la prise en charge de la nouvelle commande de menu. Cet exemple active toujours la commande de menu.

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

3. Substituez la méthode <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> dans la classe <xref:Microsoft.VisualStudio.Package.ViewFilter> pour obtenir l’objet <xref:Microsoft.VisualStudio.Package.ExpansionProvider> et appelez la méthode <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> sur cet objet.

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

     Les méthodes suivantes de la classe <xref:Microsoft.VisualStudio.Package.ExpansionProvider> sont appelées par Visual Studio dans l’ordre indiqué au cours du processus d’insertion de l’extrait de code :

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     Une fois la méthode <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> appelée, l’extrait de code a été inséré et l’objet <xref:Microsoft.VisualStudio.Package.ExpansionProvider> est dans un mode d’édition spécial utilisé pour modifier un extrait de code qui vient d’être inséré.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Insertion d’un extrait de code à l’aide d’un raccourci
 L’implémentation d’un raccourci à partir d’une liste de saisie semi-automatique est bien plus complexe que l’implémentation d’une commande de menu. Vous devez d’abord ajouter des raccourcis d’extrait de code à la liste de saisie semi-automatique des mots IntelliSense. Vous devez ensuite détecter quand un nom de raccourci d’extrait de code a été inséré à la fin de l’opération. Enfin, vous devez obtenir le titre et le chemin de l’extrait de code en utilisant le nom du raccourci et passer ces informations à la méthode <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> sur la méthode <xref:Microsoft.VisualStudio.Package.ExpansionProvider>.

 Pour ajouter des raccourcis d’extrait de code à la liste de saisie semi-automatique des mots, ajoutez-les à l’objet <xref:Microsoft.VisualStudio.Package.Declarations> de votre classe <xref:Microsoft.VisualStudio.Package.AuthoringScope>. Vous devez vous assurer que vous pouvez identifier le raccourci comme un nom d’extrait de code. Pour obtenir un exemple, consultez [procédure pas à pas : obtention d’une liste d’extraits de code installés (implémentation héritée)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

 Vous pouvez détecter l’insertion du raccourci d’extrait de code dans la méthode <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> de la classe <xref:Microsoft.VisualStudio.Package.Declarations>. Étant donné que le nom de l’extrait de code a déjà été inséré dans le fichier source, il doit être supprimé lors de l’insertion du développement. La méthode <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> prend une étendue qui décrit le point d’insertion de l’extrait de code ; Si l’étendue comprend l’intégralité du nom de l’extrait de code dans le fichier source, ce nom est remplacé par l’extrait de code.

 Voici une version d’une classe <xref:Microsoft.VisualStudio.Package.Declarations> qui gère l’insertion d’extraits de code en fonction d’un nom de raccourci. D’autres méthodes de la classe <xref:Microsoft.VisualStudio.Package.Declarations> ont été omises par souci de clarté. Notez que le constructeur de cette classe accepte un objet <xref:Microsoft.VisualStudio.Package.LanguageService>. Cela peut être passé à partir de votre version de l’objet <xref:Microsoft.VisualStudio.Package.AuthoringScope> (par exemple, votre implémentation de la classe <xref:Microsoft.VisualStudio.Package.AuthoringScope> peut prendre l’objet <xref:Microsoft.VisualStudio.Package.LanguageService> dans son constructeur et passer cet objet à votre constructeur de classe `TestDeclarations`).

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

 Lorsque le service de langage obtient le nom du raccourci, il appelle la méthode <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> pour obtenir le nom de fichier et le titre de l’extrait de code. Le service de langage appelle ensuite la méthode <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> dans la classe <xref:Microsoft.VisualStudio.Package.ExpansionProvider> pour insérer l’extrait de code. Les méthodes suivantes sont appelées par Visual Studio dans l’ordre indiqué dans la classe <xref:Microsoft.VisualStudio.Package.ExpansionProvider> au cours du processus d’insertion de l’extrait de code :

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   Pour plus d’informations sur l’obtention d’une liste d’extraits de code installés pour votre service de langage, consultez [procédure pas à pas : obtention d’une liste d’extraits de code installés (implémentation héritée)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

## <a name="implementing-the-expansionfunction-class"></a>Implémentation de la classe ExpansionFunction
 Une fonction d’expansion est une fonction nommée qui est incorporée dans un modèle d’extrait de code et retourne une ou plusieurs valeurs à placer dans un champ. Afin de prendre en charge les fonctions d’extension dans votre service de langage, vous devez dériver une classe de la classe <xref:Microsoft.VisualStudio.Package.ExpansionFunction> et implémenter la méthode <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A>. Vous devez ensuite substituer la méthode <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> dans la classe <xref:Microsoft.VisualStudio.Package.LanguageService> pour retourner une nouvelle instanciation de votre version de la classe <xref:Microsoft.VisualStudio.Package.ExpansionFunction> pour chaque fonction d’expansion que vous prenez en charge. Si vous prenez en charge une liste de valeurs possibles à partir d’une fonction d’expansion, vous devez également substituer la méthode <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> dans la classe <xref:Microsoft.VisualStudio.Package.ExpansionFunction> pour retourner une liste de ces valeurs.

 Une fonction d’expansion qui accepte des arguments ou a besoin d’accéder à d’autres champs ne doit pas être associée à un champ modifiable, car le fournisseur d’expansion peut ne pas être entièrement initialisé au moment où la fonction d’expansion est appelée. Par conséquent, la fonction d’expansion n’est pas en mesure d’obtenir la valeur de ses arguments ou de tout autre champ.

### <a name="example"></a>Exemple
 Voici un exemple de la façon dont une fonction d’expansion simple appelée `GetName` peut être implémentée. Cette fonction d’expansion ajoute un nombre à un nom de classe de base chaque fois que la fonction d’expansion est instanciée (ce qui correspond à chaque fois que l’extrait de code associé est inséré).

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
- [Fonctionnalités du service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md)
- [Inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Extraits de code](../../ide/code-snippets.md)
- [Procédure pas à pas : Obtention d’une liste d’extraits de code installés (implémentation héritée)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)