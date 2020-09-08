When deploying piecemeal from within the Web IDE, first create a service instance of the xsuaa.

```
xs cs xsuaa default mta_purenode_uaa
```

Note:  If you first build the project to an MTAR and then deploy it to the local system, the above will be created as a by-product of the deploy.


NodeJS Docs: [The SAP HANA XS Advanced JavaScript Run Time](https://help.sap.com/viewer/4505d0bdaf4948449b7f7379d24d0f0d/2.0.03/en-US/18c01923b738416d8ec2eaa3eae2a4bf.html)

# Build Command:
```
mkdir -p mta_archives
mbt build -p=xsa -t=mta_archives --mtar=purenode_xsa.mtar
mbt build -p=cf -t=mta_archives --mtar=purenode_cf.mtar
```

# Deploy Command:
```
xs deploy mta_archives/purenode_xsa.mtar -f
cf deploy mta_archives/purenode_cf.mtar -f -e dedicated_cf.mtaext
```

# Subsequent Build+Deploy Commands:
```
mbt build -p=xsa -t=mta_archives --mtar=purenode_xsa.mtar ; xs deploy mta_archives/purenode_xsa.mtar -f
mbt build -p=cf -t=mta_archives --mtar=purenode_cf.mtar ; cf deploy mta_archives/purenode_cf.mtar -f
```

# Undeploy Command:
```
xs undeploy bump -f --delete-services
cf undeploy bump -f --delete-services
```
