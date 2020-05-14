---
title: 'Comment : Enregistrez une bibliothèque auprès du gestionnaire d’objets Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4bd1032d2ba67a0c0f3338560a80038ed3215531
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707943"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Comment : Enregistrer une bibliothèque auprès du gestionnaire de l’objet
Les outils de navigation des symboles, tels que **Class View**, **Object Browser**, Call **Browser** et Find **Symbol Results,** vous permettent de visualiser des symboles dans votre projet ou dans des composants externes. Les symboles incluent des espaces de nom, des classes, des interfaces, des méthodes et d’autres éléments de langage. Les bibliothèques suivent ces symboles [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et les exposent au gestionnaire d’objets qui peuple les outils avec les données.

 Le gestionnaire d’objets garde une trace de toutes les bibliothèques disponibles. Chaque bibliothèque doit s’inscrire auprès du gestionnaire d’objets avant de fournir des symboles pour les outils de navigation des symboles.

 En règle générale, vous enregistrez une bibliothèque lorsqu’un VSPackage se charge. Cependant, il peut être fait à un autre moment au besoin. Vous désenregistrez la bibliothèque lorsque le VSPackage ferme.

 Pour enregistrer une bibliothèque, utilisez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> méthode. Pour une bibliothèque de <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> code gérée, utilisez la méthode.

 Pour désinscrire une <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> bibliothèque, utilisez la méthode.

 Pour obtenir une référence au <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>gestionnaire d’objets, `GetService` passez l’ID de service à la <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> méthode.

## <a name="register-and-unregister-a-library-with-the-object-manager"></a>Inscrivez-vous et désinscrire une bibliothèque auprès du gestionnaire de l’objet

### <a name="to-register-a-library-with-the-object-manager"></a>Pour enregistrer une bibliothèque auprès du gestionnaire de l’objet

1. Créez une bibliothèque.

    ```vb
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing
    Private m_nLibraryCookie As UInteger = 0
    ' Create Library.
    m_CallBrowserLibrary = New CallBrowser.Library()
    ```

    ```csharp
    private CallBrowser.Library m_CallBrowserLibrary = null;
    private uint m_nLibraryCookie = 0;
    // Create Library.
    m_CallBrowserLibrary = new CallBrowser.Library();

    ```

2. Obtenir une référence à <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> un objet <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> du type et appeler la méthode.

    ```vb
    Private Sub RegisterLibrary()
        If m_nLibraryCookie <> 0 Then
            Throw New Exception("Library already registered with Object Manager")
        End If

        ' Obtain a reference to IVsObjectManager2 type object.
        Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)
        If objManager Is Nothing Then
            Throw New NullReferenceException("GetService failed for SVsObjectManager")
        End If

        Try
            Dim hr As Integer = objManager.RegisterSimpleLibrary(m_CallBrowserLibrary, m_nLibraryCookie)
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr)
        Catch e As Exception
            ' Code to handle any CLS-compliant exception.
            Trace.WriteLine(e.Message)
            Throw
        End Try
    End Sub
    ```

    ```csharp
    private void RegisterLibrary()
    {
        if (m_nLibraryCookie != 0)
            throw new Exception("Library already registered with Object Manager");

        // Obtain a reference to IVsObjectManager2 type object.
        IVsObjectManager2 objManager =
                          GetService(typeof(SVsObjectManager)) as IVsObjectManager2;
        if (objManager == null)
            throw new NullReferenceException("GetService failed for SVsObjectManager");

        try
        {
            int hr =
                objManager.RegisterSimpleLibrary(m_CallBrowserLibrary,
                                                 out m_nLibraryCookie);
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);
        }
        catch (Exception e)
        {
            // Code to handle any CLS-compliant exception.
            Trace.WriteLine(e.Message);
            throw;
        }
    }

    ```

### <a name="to-unregister-a-library-with-the-object-manager"></a>Désenregistrer une bibliothèque avec le gestionnaire de l’objet

1. Obtenir une référence à <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> un objet <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> du type et appeler la méthode.

    ```vb
    Private Sub UnregisterLibrary()
        If m_nLibraryCookie <> 0 Then
            ' Obtain a reference to IVsObjectManager2 type object.
            Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)
            If objManager Is Nothing Then
                Throw New NullReferenceException("GetService failed for SVsObjectManager")
            End If

            Try
                objManager.UnregisterLibrary(m_nLibraryCookie)
            Catch e As Exception
                ' Code to handle any CLS-compliant exception.
                Trace.WriteLine(e.Message)
                Throw
            Finally
                m_nLibraryCookie = 0
            End Try
        End If
    End Sub
    ```

    ```csharp
    private void UnregisterLibrary()
    {
        if (m_nLibraryCookie != 0)
        {
            // Obtain a reference to IVsObjectManager2 type object.
            IVsObjectManager2 objManager = GetService(typeof(SVsObjectManager)) as IVsObjectManager2;
            if (objManager == null)
                throw new NullReferenceException("GetService failed for SVsObjectManager");

            try
            {
                objManager.UnregisterLibrary(m_nLibraryCookie);
            }
            catch (Exception e)
            {
                // Code to handle any CLS-compliant exception.
                Trace.WriteLine(e.Message);
                throw;
            }
            finally
            {
                m_nLibraryCookie = 0;
            }
        }
    }

    ```

## <a name="see-also"></a>Voir aussi
- [Héritage service linguistique extéabilité](../../extensibility/internals/legacy-language-service-extensibility.md)
- [Soutenir les outils de navigation des symboles](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Comment : Exposer les listes de symboles fournis par la bibliothèque au gestionnaire d’objets](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
