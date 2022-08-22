# XIVITA DalaDocker
un container docker basato su `Dotnet/SDK:<ver>-alpine`per lo sviluppo di progetti Dotnet che richiedono la libreria [Dalamud](https://github.com/goatcorp/Dalamud).
Lo scopo primario di questa immagine è per lo sviluppo di [development containers](https://docs.github.com/en/codespaces/setting-up-your-project-for-codespaces/introduction-to-dev-containers) e ambienti CI/CD.

## Requisiti
Per compilare un progetto che usa Dalamud compreso dentro questo container, nei vostri progetti dovete usare la variabile `DalamudLibPath` e avere lo snippet di codice dentro al vostro file csproj che trovate quì di seguito:
```
<PropertyGroup Condition="'$([System.Runtime.InteropServices.RuntimeInformation]::IsOSPlatform($([System.Runtime.InteropServices.OSPlatform]::Linux)))'">
    <DalamudLibPath>$(DALAMUD_HOME)/</DalamudLibPath>
    <CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>
</PropertyGroup>
```
## Uso
Questa immagine viene pubblicata in 2 tag seprati, `latest` e `staging` che ovviamente contengono due versioni differenti della libreria Dalamud. Tutti i files sorgente sono presi dal repository ufficiale [Dalamud-Distrib](https://github.com/goatcorp/dalamud-distrib).

### Latest
Latest è la versione stabile e corrente di Dalamud che può essere usata aggiungendo lo snippet di codice che trovate di seguito:
```
FROM ghcr.io/AHDCreative/xivita-daladocker:latest
```
### Staging
Stagin è la versione sperimentale della libreria Dalamud. Se volete aggiungerla al vostro progetto, copiate lo snippet seguente:
```
FROM ghcr.io/AHDCreative/xivita-daladocker:staging
```
## Aggiornamento dei Container
Tutti i container vengono aggiornati su base settimanale. Per quanto riguarda la versione di Dotnet, sarà incrementata quando sarà compatibile con la libreria e ci sarà una immagine base disponibile.