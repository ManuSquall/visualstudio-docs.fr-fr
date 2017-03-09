---
title: "Exportation de param&#232;tres | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDE, exportation de paramètres à l’aide d’une infrastructure de package gérée"
  - "infrastructure de package gérée, exportation des paramètres d’environnement"
  - "paramètres utilisateur [SDK Visual Studio], exportation à l’aide d’une infrastructure de package gérée"
  - "paramètres IDE, exportation à l’aide d’une infrastructure de package gérée"
ms.assetid: cb3ddb38-4e75-4f05-a83a-8396345bc36c
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# Exportation de param&#232;tres
L'environnement de développement intégré \(IDE\) de \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilise les classes qui implémentent l'interface et les classes d' <xref:Microsoft.VisualStudio.Shell.IProfileManager> stockées comme prenant en charge une implémentation donnée d'un VSPackage d'enregistrer l'état d'un VSPackage.  
  
 Comme l'IDE instancie la classe qui implémente l'interface d' <xref:Microsoft.VisualStudio.Shell.IProfileManager> pour prendre en charge les paramètres, <xref:Microsoft.VisualStudio.Shell.IProfileManager> doit être implémenté dans une classe distincte.  
  
> [!NOTE]
>  n'implémentez pas <xref:Microsoft.VisualStudio.Shell.IProfileManager> sur la classe qui implémente <xref:Microsoft.VisualStudio.Shell.Package>.  
  
### pour implémenter l'exportation des paramètres  
  
1.  déclarez la classe qui implémente les paramètres de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  
  
     Déclarez une classe comme implémenter l'interface de <xref:Microsoft.VisualStudio.Shell.IProfileManager> et fournissez\-lui GUID.  
  
    > [!NOTE]
    >  les classes qui implémentent <xref:Microsoft.VisualStudio.Shell.IProfileManager> doivent également implémenter <xref:System.ComponentModel.IComponent>.  Cette opération peut être effectuée en dérivant la classe d' <xref:System.ComponentModel.Component>.  
  
     Par exemple :  
  
    ```  
    [Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
    internal class MyPackageProfileManager : Component, IProfileManager   
    ```  
  
2.  Vérifier que la classe qui implémente les paramètres obtient les informations d'état correctes.  cette procédure est spécifique à chaque VSPackage, et peut impliquer obtenir l'état de l'automation, interroger des clés de Registre, ou interroger le VSPackage.  
  
     En général, comme dans l'exemple suivant, utilisez l'implémentation de la méthode de <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> pour valider et présenter les informations d'état d'un VSPackage.  
  
    > [!NOTE]
    >  La méthode d' <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> est également appelée par l'IDE lorsqu'il initialise le VSPackage qu'il prend en charge.  
  
     Dans ce cas, l'implémentation de la méthode de <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> rend ces éléments :  
  
    -   Obtient l'accès aux informations d'état dans la configuration et les données de configuration actuelles d'un VSPackage stockées dans le Registre.  
  
        ```vb#  
        Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
        Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
        Dim rootKey As RegistryKey = package.UserRegistryRoot  
        ```  
  
        ```c#  
        MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
        Package package = GetService(typeof(Package)) as Package;  
        RegistryKey rootKey = package.UserRegistryRoot;  
        ```  
  
    -   Selon la valeur retournée par la méthode d' `MakeCurrentSettingTheDefault` d'un VSPackage, il les mises à jour les paramètres du Registre à l'aide de l'état actuel d'un VSPackage, ou l'état à l'aide de les paramètres du Registre.  
  
        ```vb#  
        If mySvc.MyPackage.MakeCurrentSettingTheDefault() Then   
            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
        Else   
            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).LoadState(pbrsKey)   
        End If  
        ```  
  
        ```c#  
        if (mySvc.MyPackage.MakeCurrentSettingTheDefault()){  
          ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
        }else{  
          ((IComPropertyBrowser)mySvc.MyPackage.packageState).LoadState(pbrsKey);  
        }  
        ```  
  
         Pour plus de simplicité dans cet exemple, à moins que la méthode d' `MakeCurrentSettingsTheDefault` retourne `true`, l'état actuel est toujours réinitialisé à la valeur par défaut qui sont stockées dans le Registre.  
  
3.  Vérifier que la classe qui implémente les paramètres rend également l'état sur le disque.  
  
     l'écriture réelle des informations d'état au fichier sur disque de paramètres doit toujours être effectuée par l'implémentation de classe de la méthode d' <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> .  les détails d'une opération de writer de paramètres dépendent de l'implémentation.  
  
     Toutefois, la classe doit obtenir l'accès aux informations d'état et doit utiliser l'interface fournie d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> pour enregistrer des données dans le fichier de paramètres.  
  
     En général, comme dans l'exemple suivant, l'implémentation de la méthode de <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> ne valide pas les informations d'état.  la validation est exécutée dans la méthode d' <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> .  au lieu de cela, l'implémentation obtient simplement l'accès aux informations d'état et l'écrit, dans ce cas, comme données de chaîne.  
  
    ```vb#  
    Dim mySvc As MyPackageService = TryCast(GetService(GetType(MyPackage)), MyPackageService)   
    If mySvc IsNot Nothing Then   
        ' Information is stored in a StateObject   
        Dim myState As StateObject = mySvc.MyPackage.packageState   
        writer.WriteSettingString("PbrsAlpha", (If(myState.SortState = SortState.Alphabetical, "1", "0")))   
        writer.WriteSettingString("PbrsShowDesc", (If(myState.HelpVisible, "1", "0")))   
    End If  
  
    ```  
  
    ```c#  
    MyPackageService mySvc = GetService(typeof(MyPackage)) as MyPackageService;  
    if (mySvc != null) {  
      // Information is stored in a StateObject  
      StateObject myState = mySvc.MyPackage.packageState;  
     writer.WriteSettingString(   
                                "PbrsAlpha",   
                                (myState.SortState == SortState.Alphabetical ? "1" : "0"));  
      writer.WriteSettingString(   
                                "PbrsShowDesc",   
                                (myState.HelpVisible ? "1" : "0"));  
    }  
    ```  
  
     Les détails d'implémentation sont les suivantes :  
  
    -   Outre les données explicitement entrées et transparentes à l'implémentation de la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> , l'API de paramètres enregistre également des informations de version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  Par conséquent, stocké des paramètres peuvent être comparées avec la version de l'IDE qui les a générés lors de l'importation de paramètres.  
  
    -   La valeur de l'argument d' `pszSettingName` fourni à une méthode d'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> doit identifier de manière unique chaque élément de données stocké dans une catégorie de paramètres.  
  
        > [!NOTE]
        >  Les noms doivent être uniques dans la portée de la classe d'implémentation.  L'IDE utilise le GUID de la classe qui implémente les paramètres et la valeur d' `pszSettingName` pour identifier chaque paramètre enregistré.  Si plusieurs méthodes d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> qui ont la même valeur d' `pszSettingName` sont appelées, la valeur d'origine est remplacée dans le fichier de paramètres.  
  
    -   Le fichier de paramètres prend en charge l'accès aux données aléatoires, l'ordre des opérations en lecture et en écriture n'est pas importante.  Dans l'exemple suivant, l'ordre des opérations de writer dans l'implémentation de la méthode de <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> est opposée des opérations de lecture dans la méthode d' <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> .  
  
    -   Si l'implémentation peut des données qui mappent dans l'un des quatre formats pris en charge, il n'y a aucune restriction sur le nombre et le type de données peut être écrit.  
  
        > [!NOTE]
        >  la répartition des tâches entre <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> et les méthodes d' <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> dépend de l'implémentation et est quelque peu arbitraire.  Par exemple, l'implémentation peut être réécrite en utilisant une implémentation vide de la méthode d' <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> et en faisant exécuter toutes les requêtes de Registre et d'état dans la méthode d' <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> .  
  
4.  Enregistrez les paramètres implémentant la classe en fournissant la prise en charge à un VSPackage.  
  
     Appliquez une instance d' <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> générée à l'aide de <xref:System.Type> de la classe qui implémente <xref:Microsoft.VisualStudio.Shell.IProfileManager> à l'implémentation d'un VSPackage <xref:Microsoft.VisualStudio.Shell.Package> .  
  
    ```vb#  
    <ProvideProfile(GetType(MyPackageProfileManager), "CoreUI", "MyPackage", 1004, 1004, False)> _   
    <Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")> _   
    Class MyPackage   
        Inherits Package   
    End Class  
    ```  
  
    ```c#  
    [ProvideProfile(typeof(MyPackageProfileManager), "CoreUI", "MyPackage", 1004, 1004, false)]  
    [Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")]  
    class MyPackage: Package   
    ```  
  
     Dans ce cas, l'attribut signale à l'IDE que la classe d' `MyPackageProfileManager` fournit une implémentation de paramètres à la classe d' `MyPackage` .  Le point de paramètres personnalisés dans le Registre est créé sous \\Software\\Microsoft\\VisualStudio HKLM \\*version*\\UserSettings\\ CoreUI\_MyPackage, où *version* est la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], par exemple, 10,0.  
  
     Pour plus d'informations, consultez [Prise en charge pour les paramètres utilisateur](../extensibility/internals/support-for-user-settings.md) et <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## Exemple  
 l'exemple suivant implémente <xref:Microsoft.VisualStudio.Shell.IProfileManager> sur une classe.  
  
```vb#  
Imports System   
Imports System.Runtime.InteropServices   
Imports Microsoft.VisualStudio.Shell   
Imports Microsoft.VisualStudio.Shell.Interop   
Imports Microsoft.Win32   
Imports myPackageNameSpace   
Namespace myProfileManagerNameSpace  
  
    <Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")> _   
    Friend Class MyPackageProfileManager   
        Inherits System.ComponentModel.Component   
        Implements IProfileManager   
        Friend Const m_supportVer As Integer = 8   
        Public Sub SaveSettingsToXml(ByVal writer As IVsSettingsWriter)   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(MyPackage)), MyPackageService)   
            If mySvc IsNot Nothing Then   
                ' Information is stored in a StateObject.   
                Dim myState As StateObject = mySvc.MyPackage.packageState   
                writer.WriteSettingString("PbrsAlpha", (If(myState.SortState = SortState.Alphabetical, "1", "0")))   
                writer.WriteSettingString("PbrsShowDesc", (If(myState.HelpVisible, "1", "0")))   
            End If   
        End Sub   
  
        Public Sub LoadSettingsFromXml(ByVal reader As IVsSettingsReader)   
  
            Dim pnMajor As Integer, pnMinor As Integer, pnBuild As Integer   
            ' First, check if data is obtained from the correct major version   
            reader.ReadVersion(pnMajor, pnMinor, pnBuild)   
            If pnMajor <> m_supportVer Then   
                reader.ReportError("Unsupported Version")   
            Else   
                Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
                If mySvc IsNot Nothing Then   
                    Dim value As String   
                    Dim myState As StateObject = mySvc.MyPackage.packageState   
                    reader.ReadSettingString("PbrsShowDesc", value)   
                    ' Not all values must be present.   
                    If value Is Nothing OrElse value = "" Then   
                        reader.ReportError("Unable to Help Visibility Setting")   
                    Else   
                        myState.HelpVisible = Not value.Equals("0")   
                    End If   
                    reader.ReadSettingString("PbrsAlpha", value)   
                    ' Not all values must be present.   
                    If value Is Nothing OrElse value = "" Then   
                        reader.ReportError("Unable to Retrieve Sort Value")   
                    Else   
                        If Not value.Equals("0") Then   
                            myState.SortState = SortState.Alphabetical   
                        Else   
                            myState.SortState = SortState.Categorized   
                        End If   
                    End If   
                End If   
            End If   
        End Sub   
  
        Public Sub SaveSettingsToStorage()   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
            Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
            Dim rootKey As RegistryKey = package.UserRegistryRoot   
  
            If mySvc.MyPackage.packageState IsNot Nothing Then   
                Using rootKey   
                    Using pbrsKey As RegistryKey = rootKey.CreateSubKey(Me.[GetType]().Name)   
                        Using pbrsKey   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
                        End Using   
                    End Using   
                End Using   
            End If   
        End Sub   
  
        Public Sub LoadSettingsFromStorage()   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
            Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
            Dim rootKey As RegistryKey = package.UserRegistryRoot   
            Using rootKey   
                Dim pbrsKey As RegistryKey = rootKey.OpenSubKey(Me.[GetType]().Name)   
                If pbrsKey IsNot Nothing Then   
                    Using pbrsKey   
                        If mySvc.MyPackage.MakeCurrentSettingTheDefault() Then   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
                        Else   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).LoadState(pbrsKey)   
                        End If   
                    End Using   
                End If   
            End Using   
        End Sub   
    End Class   
End Namespace   
  
Convert C# to VB.NET  
  
```  
  
```c#  
namespace myProfileManagerNameSpace  {  
  
  using System;  
  using System.Runtime.InteropServices;  
  using Microsoft.VisualStudio.Shell;  
  using Microsoft.VisualStudio.Shell.Interop;  
  using Microsoft.Win32;  
  using myPackageNameSpace;  
  
  [Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
  internal class MyPackageProfileManager : System.ComponentModel.Component , IProfileManager {  
    internal const int m_supportVer = 8;  
    public void SaveSettingsToXml(IVsSettingsWriter writer) {  
      MyPackageService mySvc = GetService(typeof(MyPackage)) as MyPackageService;  
      if (mySvc != null) {  
        // Information is stored in a StateObject.  
        StateObject myState = mySvc.MyPackage.packageState;  
        writer.WriteSettingString(   
                                  "PbrsAlpha",   
                                  (myState.SortState == SortState.Alphabetical ? "1" : "0"));  
        writer.WriteSettingString(   
                                  "PbrsShowDesc",   
                                  (myState.HelpVisible ? "1" : "0"));  
      }  
    }  
  
    public void LoadSettingsFromXml(IVsSettingsReader reader)  
    {  
  
      int pnMajor, pnMinor, pnBuild;  
      // First, check if data is obtained from the correct major version   
      reader.ReadVersion(pnMajor, pnMinor, pnBuild);  
      if (pnMajor != m_supportVer){  
        reader.ReportError("Unsupported Version");  
      }else{  
        MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
        if (mySvc != null){  
          string value;  
          StateObject myState = mySvc.MyPackage.packageState;  
          reader.ReadSettingString("PbrsShowDesc", out value);  
          // Not all values must be present.  
          if (value == null || value == ""){  
              reader.ReportError("Unable to Help Visibility Setting");  
          }else{  
            myState.HelpVisible = !value.Equals("0");  
          }  
          reader.ReadSettingString("PbrsAlpha", out value);  
          // Not all values must be present.  
          if (value == null || value == ""){  
              reader.ReportError("Unable to Retrieve Sort Value");  
          }else{  
            if (!value.Equals("0")){  
              myState.SortState = SortState.Alphabetical;  
            }else{  
              myState.SortState = SortState.Categorized;  
            }  
          }  
        }  
      }  
    }  
  
    public void SaveSettingsToStorage() {  
      MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
      Package package = GetService(typeof(Package)) as Package;  
      RegistryKey rootKey = package.UserRegistryRoot;  
  
      if (mySvc.MyPackage.packageState != null) {  
        using (rootKey) {  
          using(RegistryKey pbrsKey = rootKey.CreateSubKey(this.GetType().Name)) {  
            using (pbrsKey) {  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
            }  
          }  
        }  
      }  
    }  
  
    public void LoadSettingsFromStorage() {  
      MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
      Package package = GetService(typeof(Package)) as Package;  
      RegistryKey rootKey = package.UserRegistryRoot;  
      using (rootKey) {  
        RegistryKey pbrsKey = rootKey.OpenSubKey(this.GetType().Name);  
        if (pbrsKey != null) {  
          using (pbrsKey) {  
            if (mySvc.MyPackage.MakeCurrentSettingTheDefault()){  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
            }else{  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).LoadState(pbrsKey);  
            }  
          }  
        }  
      }  
    }  
  }  
}  
```  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.IProfileManager>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>   
 [Importation des paramètres](/visual-cpp/misc/importing-settings)   
 [Prise en charge pour les paramètres utilisateur](../extensibility/internals/support-for-user-settings.md)