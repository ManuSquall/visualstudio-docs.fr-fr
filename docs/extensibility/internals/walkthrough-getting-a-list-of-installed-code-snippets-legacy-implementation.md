---
title: Obtenir une liste de Snippets de code installés (Héritage) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3d5ef857973555c4b2d201f98957bd2c39328b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703652"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>Procédure pas à pas : obtention d’une liste d’extraits de code installés (implémentation héritée)
Un extrait de code est un morceau de code qui peut être inséré dans le tampon source soit avec une commande de menu (qui permet de choisir parmi une liste de extraits de code installés) ou en sélectionnant un raccourci extrait d’une liste d’achèvement IntelliSense.

 La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> méthode obtient tous les extraits de code pour une langue spécifique GUID. Les raccourcis pour ces extraits peuvent être insérés dans une liste d’achèvement IntelliSense.

 Consultez [Support for Code Snippets in a Legacy Language Service](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) pour plus de détails sur la mise en œuvre de extraits de code dans un cadre de forfait géré (MPF) service linguistique.

### <a name="to-retrieve-a-list-of-code-snippets"></a>Pour récupérer une liste de extraits de code

1. Le code suivant montre comment obtenir une liste de extraits de code pour une langue donnée. Les résultats sont stockés <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> dans un éventail de structures. Cette méthode utilise <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> statique <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> pour obtenir l’interface du service. Toutefois, vous pouvez également utiliser le fournisseur de services <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> donné à votre VSPackage et appeler la méthode.

    ```csharp
    using System;
    using System.Collections;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Package;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.TextManager.Interop;

    [Guid("00000000-0000-0000-0000-000000000000")] //create a new GUID for the language service
    namespace TestLanguage
    {
        class TestLanguageService : LanguageService
        {
            private void GetSnippets(Guid languageGuid,
                                     ref ArrayList expansionsList)
            {
                IVsTextManager textManager = (IVsTextManager)Package.GetGlobalService(typeof(SVsTextManager));
                if (textManager != null)
                {
                    IVsTextManager2 textManager2 = (IVsTextManager2)textManager;
                    if (textManager2 != null)
                    {
                        IVsExpansionManager expansionManager = null;
                        textManager2.GetExpansionManager(out expansionManager);
                        if (expansionManager != null)
                        {
                            // Tell the environment to fetch all of our snippets.
                            IVsExpansionEnumeration expansionEnumerator = null;
                            expansionManager.EnumerateExpansions(languageGuid,
                            0,     // return all info
                            null,    // return all types
                            0,     // return all types
                            1,     // include snippets without types
                            0,     // do not include duplicates
                            out expansionEnumerator);
                            if (expansionEnumerator != null)
                            {
                                // Cache our expansions in a VsExpansion array
                                uint count   = 0;
                                uint fetched = 0;
                                VsExpansion expansionInfo = new VsExpansion();
                                IntPtr[] pExpansionInfo   = new IntPtr[1];

                                // Allocate enough memory for one VSExpansion structure. This memory is filled in by the Next method.
                                pExpansionInfo[0] = Marshal.AllocCoTaskMem(Marshal.SizeOf(expansionInfo));

                                expansionEnumerator.GetCount(out count);
                                for (uint i = 0; i < count; i++)
                                {
                                    expansionEnumerator.Next(1, pExpansionInfo, out fetched);
                                    if (fetched > 0)
                                    {
                                        // Convert the returned blob of data into a structure that can be read in managed code.
                                        expansionInfo = (VsExpansion)Marshal.PtrToStructure(pExpansionInfo[0], typeof(VsExpansion));

                                        if (!String.IsNullOrEmpty(expansionInfo.shortcut))
                                        {
                                            expansionsList.Add(expansionInfo);
                                        }
                                    }
                                }
                                Marshal.FreeCoTaskMem(pExpansionInfo[0]);
                            }
                        }
                    }
                }
            }
        }
    }
    ```

### <a name="to-call-the-getsnippets-method"></a>Pour appeler la méthode GetSnippets

1. La méthode suivante montre `GetSnippets` comment appeler la méthode à l’achèvement d’une opération d’analyse. La <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> méthode est appelée après une opération d’analyse qui a été commencée avec la raison <xref:Microsoft.VisualStudio.Package.ParseReason>.

> [!NOTE]
> La `expansionsList` liste de tableau est mise en cache pour des raisons de performance. Les modifications apportées aux extraits ne sont pas reflétées dans la liste tant que le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]service linguistique n’est pas arrêté et rechargé (par exemple, en s’arrêtant et en redémarrant).

```csharp
class TestLanguageService : LanguageService
{
    private ArrayList expansionsList;

    public override void OnParseComplete(ParseRequest req)
    {
        if (this.expansionsList == null)
        {
            this.expansionsList = new ArrayList();
            GetSnippets(this.GetLanguageServiceGuid(),
                ref this.expansionsList);
        }
    }
}
```

### <a name="to-use-the-snippet-information"></a>Pour utiliser les informations d’extrait

1. Le code suivant montre comment utiliser les informations `GetSnippets` d’extrait retournées par la méthode. La `AddSnippets` méthode est appelée à partir du parseur en réponse à toute raison d’analyse qui est utilisé pour remplir une liste de extraits de code. Cela devrait avoir lieu après que l’analyse complète a été faite pour la première fois.

     La `AddDeclaration` méthode dresse une liste de déclarations qui est plus tard affichée dans une liste d’achèvement.

     La `TestDeclaration` classe contient toutes les informations qui peuvent être affichées dans une liste d’achèvement ainsi que le type de déclaration.

    ```csharp
    class TestAuthoringScope : AuthoringScope
    {
        public void AddDeclarations(TestDeclaration declaration)
        {
            if (m_declarations == null)
                m_declarations = new List<TestDeclaration>();
            m_declarations.Add(declaration);
         }
    }
    class TestDeclaration
    {
        private string m_name;
        private string m_description;
        private string m_type;

        public TestDeclaration(string name, string desc, string type)
        {
            m_name = name;
            m_description = desc;
            m_type = type;
        }

    class TestLanguageService : LanguageService
    {
        internal void AddSnippets(ref TestAuthoringScope scope)
        {
            if (this.expansionsList != null && this.expansionsList.Count > 0)
            {
                int count = this.expansionsList.Count;
                for (int i = 0; i < count; i++)
                {
                    VsExpansion expansionInfo = (VsExpansion)this.expansionsList[i];
                    scope.AddDeclaration(new TestDeclaration(expansionInfo.title,
                         expansionInfo.description,
                         "snippet"));
                }
            }
        }
    }

    ```

## <a name="see-also"></a>Voir aussi
- [Prise en charge des extraits de code dans un service de langage hérité](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)
