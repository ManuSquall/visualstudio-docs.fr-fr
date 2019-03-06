---
title: 'Procédure : Modifier des fichiers Web.Config pour instrumenter et profiler des applications web ASP.NET compilées dynamiquement | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a92e5692-2183-4ae3-9431-b067c6a7aab4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 925112de25a127d4664bb66d602ca137ad624f70
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616688"
---
# <a name="how-to-modify-webconfig-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications"></a>Procédure : Modifier des fichiers Web.Config pour instrumenter et profiler des applications web ASP.NET compilées dynamiquement
Vous pouvez utiliser la méthode d’instrumentation des outils de profilage de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour collecter des données de minutage détaillées, des données d’allocation de mémoire .NET et des données de durée de vie des objets .NET à partir d’applications web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilées dynamiquement.

 Cette rubrique décrit comment modifier le fichier de configuration *web.config* pour activer l’instrumentation et le profilage d’applications web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

> [!NOTE]
>  Vous n’êtes pas obligé de modifier le fichier *web.config* quand vous utilisez la méthode de profilage par échantillonnage, ou quand vous souhaitez instrumenter un module [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] précompilé.

 La racine d’un fichier *web.config* est l’élément **configuration**. Pour instrumenter et profiler une application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilée dynamiquement, vous devez ajouter ou modifier les éléments suivants :

- Un élément **configuration/runtime/assemblyBinding/dependentAssembly** qui identifie l’assembly Microsoft.VisualStudio.Enterprise.ASPNetHelper qui contrôle le profilage. L’élément **dependentAssembly** contient deux éléments enfants : **assemblyIdentity** et **codeBase**.

- Un élément **configuration/system.web/compilation** qui identifie l’étape de compilation de post-traitement du profileur pour l’assembly cible.

- Deux éléments **add** qui identifient l’emplacement des outils de profilage sont ajoutés à la section **configuration/appSettings**.

  Nous vous recommandons de créer une copie du fichier *web.config* d’origine que vous pourrez utiliser pour restaurer la configuration de l’application.

### <a name="to-add-the-aspnethelper-assembly-as-a-configurationruntimeassemblybindingdependentassembly-element"></a>Pour ajouter l’assembly ASPNetHelper en tant qu’élément configuration/runtime/assemblyBinding/dependentAssembly

1. Si nécessaire, ajoutez l’élément **runtime** en tant qu’élément enfant de l’élément **configuration** ; sinon, passez à l’étape suivante.

    L’élément **runtime** n’a pas d’attributs. L’élément **configuration** ne peut avoir qu’un seul élément enfant **runtime**.

2. Si nécessaire, ajoutez l’élément **assemblyBinding** en tant qu’élément enfant de l’élément **runtime** ; sinon, passez à l’étape suivante.

    L’élément **runtime** ne peut avoir qu’un seul élément **assemblyBinding**.

3. Ajoutez le nom et la valeur d’attribut suivants à l’élément **assemblyBinding** :


   | Nom d'attribut | Valeur d'attribut |
   |----------------|--------------------------------------|
   | **Xmlns** | **urn:schemas-microsoft-com:asm.v1** |


4. Ajoutez un élément **dependentAssembly** en tant qu’élément enfant de l’élément **assemblyBinding**.

    L’élément **dependentAssembly** n’a pas d’attributs.

5. Ajoutez un élément **assemblyIdentity** en tant qu’enfant de l’élément **dependentAssembly**.

6. Ajoutez les noms et les valeurs d’attributs suivants à l’élément **assemblyIdentity** :


   | Nom d'attribut | Valeur d'attribut |
   |--------------------| - |
   | **name** | **Microsoft.VisualStudio.Enterprise.ASPNetHelper** |
   | **PublicKeyToken** | **b03f5f7f11d50a3a** |
   | **culture** | **Neutral** |


7. Ajoutez un élément **codeBase** en tant qu’enfant de l’élément **dependentAssembly**.

8. Ajoutez les noms et les valeurs d’attributs suivants à l’élément **codeBase** :

   |Nom d'attribut|Valeur d'attribut|
   |--------------------|---------------------|
   |**version**|**10.0.0.0**|
   |**href**|`PathToASPNetHelperDll`|

    `PathToASPNetHelperDll` est l’URL du fichier Microsoft.VisualStudio.Enterprise.ASPNetHelper.dll. Si [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est installé à l’emplacement par défaut, la valeur **href** doit être `C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL`.

```xml
    <configuration>
        <runtime>
            <assemblyBinding
                xmlns="urn:schemas-microsoft-com:asm.v1"
            >
                <dependentAssembly>
                    <assemblyIdentity name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"
                        publicKeyToken="b03f5f7f11d50a3a"
                        culture="neutral"
                    />
                    <codeBase
                        version="10.0.0.0"
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"
                    />
                </dependentAssembly>
            </assemblyBinding>
        </runtime>
```

### <a name="to-add-the-profiler-post-process-step-to-the-configurationsystemwebcompilation-element"></a>Pour ajouter l’étape de post-traitement du profileur à l’élément configuration/system.web/compilation

1.  Si nécessaire, ajoutez l’élément **system.web** en tant qu’élément enfant de l’élément **configuration** ; sinon, passez à l’étape suivante.

     L’élément **system.web** n’a pas d’attributs. L’élément **configuration** ne peut avoir qu’un seul élément enfant **system.web**.

2.  Si nécessaire, ajoutez l’élément **compilation** en tant qu’élément enfant de l’élément **system.web** ; sinon, passez à l’étape suivante.

     L’élément **system.web** ne peut avoir qu’un seul élément enfant **compilation**.

3.  Supprimez tous les attributs existants de l’élément **compilation** et ajoutez le nom et la valeur d’attribut suivants :

    |Nom d'attribut|Valeur d'attribut|
    |--------------------|---------------------|
    |**assemblyPostProcessorType**|**Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter, Microsoft.VisualStudio.Enterprise.ASPNetHelper, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a**|

```xml
    <configuration>
        <runtime>
        . . .
        </runtime>
        <system.web>
            <compilation
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,
                    Version=10.0.0.0,
                    Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
            />
        </system.web>
    <configuration>
```

### <a name="to-add-profiler-location-settings-to-the-configurationappsettings-element"></a>Pour ajouter des paramètres d’emplacement du profileur à l’élément configuration/appSettings

1. Si nécessaire, ajoutez l’élément **appSettings** en tant qu’élément enfant de l’élément **configuration** ; sinon, passez à l’étape suivante.

    L’élément **appSettings** n’a pas d’attributs. L’élément **configuration** ne peut avoir qu’un seul élément enfant **appSettings**.

2. Ajoutez un élément **add** en tant qu’enfant de l’élément **appSettings**.

3. Ajoutez les noms et les valeurs d’attributs suivants à l’élément **add** :


   | Nom d'attribut | Valeur d'attribut |
   |----------------| - |
   | **key** | **Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation** |
   | **value** | `PerformanceToolsFolder` **\VSInstr.Exe** |


4. Ajoutez un autre élément **add** en tant qu’enfant de l’élément **appSettings**.

5. Ajoutez les noms et les valeurs d’attributs suivants à cet élément **add** :

   |Nom d'attribut|Valeur d'attribut|
   |--------------------|---------------------|
   |**key**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools**|
   |**value**|`PerformanceToolsFolder`|

    `PerformanceToolsFolder` est le chemin des fichiers exécutables du profileur. Pour obtenir le chemin des outils de profilage, consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).


```xml
    <configuration>
        <runtime>
        . . .
        </runtime>
        . . .
        <system.web>
        </system.web>
        <appSettings>
            <add
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\vsinstr.exe"
        />
            <add
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\"
            />
        </appSettings>
    </configuration>
```

## <a name="example"></a>Exemple
 Le fichier *web.config* suivant active l’instrumentation et le profilage des applications web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilées dynamiquement. Cet exemple suppose qu’il n’y avait pas d’autres paramètres dans le fichier avant la modification.

```xml
<?xml version="1.0"?>
    <configuration>
        <runtime>
            <assemblyBinding
                xmlns="urn:schemas-microsoft-com:asm.v1"
            >
                <dependentAssembly>
                    <assemblyIdentity
                        name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"
                        publicKeyToken="b03f5f7f11d50a3a"
                        culture="neutral"
                    />
                    <codeBase
                        version="10.0.0.0"
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"
                    />
                </dependentAssembly>
            </assemblyBinding>
        </runtime>
        <system.web>
            <compilation
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,
                    Version=10.0.0.0,
                    Culture=neutral,
                    PublicKeyToken=b03f5f7f11d50a3a"
            />
        </system.web>
        <appSettings>
            <add
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\vsinstr.exe"
            />
            <add
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\"
            />
        </appSettings>
    </configuration>

```

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour instrumenter une application ASP.NET compilée dynamiquement et collecter des données de temporisation détaillées](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)
- [Guide pratique pour instrumenter une application ASP.NET compilée dynamiquement et collecter des données de mémoire](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)