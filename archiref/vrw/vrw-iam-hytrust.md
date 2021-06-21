---

copyright:

  years:  2020, 2021

lastupdated: "2021-04-30"

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:external: target="_blank" .external}

# HyTrust identity and access management
{: #vrw-iam-hytrust}

## HyTrust trust manifests
{: #vrw-iam-hytrust-trust}

The trust manifests provide access and control to the following resources:
- VMware vCenter Server®
- NSX-T™ administration interface
- HyTrust CloudControl

### HyTrust CloudControl trust manifest
{: #vrw-iam-hytrust-trust-manifest}

- **Default ASC_SuperAdmin rule** - Super admin role. This user has full access to all three products that are protected.
- **Cloud Admin Role** - Grants access to the vCenter.
- **Cloud Read Only** - Grants read-only access to the vCenter
- **Cloud NSX-T UI** - Grants access to manage the NSX-T objects.

### HyTrust CloudControl roles
{: #vrw-iam-hytrust-trust-roles}

| HyTrust CloudControl Role Function                       | Super Admin | Cloud Admin | NSX-T Admin | Read-only vCenter |
| ---                                                       | ---         | ---         | ---         | ---               |
| CloudControl.Asc.Login                                 | X           |             |             |                   |
| Management.CloudPlatform.Login                         | X           |             | X           |                   |
| CloudControl.Certificate.Edit                          | X           |             |             |                   |
| CloudControl.Certificate.View                          | X           |             |             |                   |
| CloudControl.Certificate.Install                       | X           |             |             |                   |
| CloudControl.Certificate.Create                        | X           |             |             |                   |
| CloudControl.CloudSystem.View                          | X           |             |             |                   |
| CloudControl.Configuration.View                        | X           |             |             |                   |
| CloudControl.Dashboard.Edit                            | X           |             |             |                   |
| CloudControl.Dashboard.View                            | X           |             |             |                   |
| CloudControl.Group.View                                | X           |             |             |                   |
| CloudControl.HardeningPolicy.Assess                    | X           |             |             |                   |
| CloudControl.HardeningPolicy.Create                    | X           |             |             |                   |
| CloudControl.HardeningPolicy.Delete                    | X           |             |             |                   |
| CloudControl.HardeningPolicy.Edit                      | X           |             |             |                   |
| CloudControl.HardeningPolicy.Remediate                 | X           |             |             |                   |
| CloudControl.HardeningPolicy.View                      | X           |             |             |                   |
| CloudControl.HardeningResults.Configure                | X           |             |             |                   |
| CloudControl.HardeningResults.View                     | X           |             |             |                   |
| CloudControl.HardeningTemplate.Clone                   | X           |             |             |                   |
| CloudControl.HardeningTemplate.Create                  | X           |             |             |                   |
| CloudControl.HardeningTemplate.Delete                  | X           |             |             |                   |
| CloudControl.HardeningTemplate.Edit                    | X           |             |             |                   |
| CloudControl.HardeningTemplate.Export                  | X           |             |             |                   |
| CloudControl.HardeningTemplate.Import                  | X           |             |             |                   |
| CloudControl.HardeningTemplate.View                    | X           |             |             |                   |
| CloudControl.Job.Halt                                  | X           |             |             |                   |
| CloudControl.Job.View                                  | X           |             |             |                   |
| CloudControl.Log.View                                  | X           |             |             |                   |
| CloudControl.Operation.View                            | X           |             |             |                   |
| Management.Password.Edit                               | X           |             |             |                   |
| CloudControl.Preference.Delete                         | X           |             |             |                   |
| CloudControl.Preference.Edit                           | X           |             |             |                   |
| CloudControl.Preference.View                           | X           |             |             |                   |
| CloudControl.Report.View                               | X           |             |             |                   |
| CloudControl.Report.Edit                               | X           |             |             |                   |
| CloudControl.Role.Create                               | X           |             |             |                   |
| CloudControl.Role.Delete                               | X           |             |             |                   |
| CloudControl.Role.Edit                                 | X           |             |             |                   |
| CloudControl.Role.View                                 | X           |             |             |                   |
| CloudControl.ContainerOrchestrator.Protect             | X           |             |             |                   |
| CloudControl.ContainerOrchestrator.Edit                | X           |             |             |                   |
| CloudControl.DockerRegistry.Protect                    | X           |             |             |                   |
| CloudControl.SecondaryApproval.View                    | X           |             |             |                   |
| CloudControl.SecondaryApproval.Approve                 | X           |             |             |                   |
| CloudControl.ContainerImageControl.Deregister          | X           |             |             |                   |
| CloudControl.ContainerImageControl.Register            | X           |             |             |                   |
| CloudControl.SoftwareUpdate.Apply                      | X           |             |             |                   |
| CloudControl.SoftwareUpdate.View                       | X           |             |             |                   |
| CloudControl.TrustManagement.EvaluateTrust             | X           |             |             |                   |
| CloudControl.TrustManifest.View                        | X           |             |             |                   |
| CloudControl.User.Create                               | X           |             |             |                   |
| CloudControl.User.Delete                               | X           |             |             |                   |
| CloudControl.User.Edit                                 | X           |             |             |                   |
| CloudControl.User.View                                 | X           |             |             |                   |
| Network.DHCP.Create                                    | X           |             | X           |                   |
| Network.DHCP.Delete                                    | X           |             | X           |                   |
| CloudControl.Proxy.Allow_Unknown_Operation             | X           |             |             |                   |
| Network.DHCP.Edit                                      | X           |             | X           |                   |
| Network.Firewall.Enable                                | X           |             | X           |                   |
| Network.Firewall.Disable                               | X           |             | X           |                   |
| Network.Firewall.Edit                                  | X           |             | X           |                   |
| Network.Firewall.Configure_Settings                    | X           |             | X           |                   |
| Network.Router.Configure_Firewall_Settings             | X           |             | X           |                   |
| Network.Firewall.Create_Policy                         | X           |             | X           |                   |
| Network.Firewall.Delete_Policy                         | X           |             | X           |                   |
| Network.Firewall.Edit_Policy                           | X           |             | X           |                   |
| Network.IPAddressGroup.Create                          | X           |             | X           |                   |
| Network.IPAddressGroup.Delete                          | X           |             | X           |                   |
| Network.IPAddressGroup.Edit                            | X           |             | X           |                   |
| Network.IPPool.Create                                  | X           |             | X           |                   |
| Network.IPPool.Delete                                  | X           |             | X           |                   |
| Network.IPPool.Edit                                    | X           |             | X           |                   |
| Network.LoadBalancer.Create                            | X           |             | X           |                   |
| Network.LoadBalancer.Delete                            | X           |             | X           |                   |
| Network.LoadBalancer.Edit                              | X           |             | X           |                   |
| Network.MacAddressGroup.Create                         | X           |             | X           |                   |
| Network.MacAddressGroup.Delete                         | X           |             | X           |                   |
| Network.MacAddressGroup.Edit                           | X           |             | X           |                   |
| Network.Object.Assign_To_ExcludeList                   | X           |             | X           |                   |
| Network.Object.UnAssign_From_ExcludeList               | X           |             | X           |                   |
| Network.SecurityGroup.Create                           | X           |             | X           |                   |
| Network.SecurityGroup.Delete                           | X           |             | X           |                   |
| Network.SecurityGroup.Edit                             | X           |             | X           |                   |
| Network.Router.Create                                  | X           |             | X           |                   |
| Network.Router.Delete                                  | X           |             | X           |                   |
| Network.Router.Edit                                    | X           |             | X           |                   |
| Network.Router.Enable_Firewall                         | X           |             | X           |                   |
| Network.Router.Disable_Firewall                        | X           |             | X           |                   |
| Network.Router.Edit_Shared_Firewall                    | X           |             | X           |                   |
| Network.Router.Edit_Firewall                           | X           |             | X           |                   |
| Network.Router.Edit_Firewall_Policy                    | X           |             | X           |                   |
| Network.Router.View_Firewall_Policy                    | X           |             | X           |                   |
| Network.Router.Create_Firewall_Policy                  | X           |             | X           |                   |
| Network.Router.Delete_Firewall_Policy                  | X           |             | X           |                   |
| Network.Router.Edit_Firewall_Rule                      | X           |             | X           |                   |
| Network.Router.View_Firewall_Rule                      | X           |             | X           |                   |
| Network.Router.Connect_Object                          | X           |             | X           |                   |
| Network.Router.Disconnect_Object                       | X           |             | X           |                   |
| Network.Monitoring.Create_Liveflow                     | X           |             | X           |                   |
| Network.NAT.Create                                     | X           |             | X           |                   |
| Network.NAT.Delete                                     | X           |             | X           |                   |
| Network.NAT.Edit                                       | X           |             | X           |                   |
| Network.Service.Create                                 | X           |             | X           |                   |
| Network.Service.Delete                                 | X           |             | X           |                   |
| Network.Service.Edit                                   | X           |             | X           |                   |
| Network.ServiceContainer.Create                        | X           |             |             |                   |
| Network.ServiceContainer.Delete                        | X           |             |             |                   |
| Network.ServiceContainer.Edit                          | X           |             |             |                   |
| Network.Switch.Connect_Object                          | X           |             | X           |                   |
| Network.Switch.Create                                  | X           |             | X           |                   |
| Network.Switch.Delete                                  | X           |             | X           |                   |
| Network.Switch.Disconnect_Object                       | X           |             | X           |                   |
| Network.Switch.Edit                                    | X           |             | X           |                   |
| Compute.VApp.Power_off                                 | X           | X           |             |                   |
| Compute.UpdateManager.View                             | X           |             |             |                   |
| Management.Library.Update                              | X           | X           |             |                   |
| Management.Profile.Edit                                | X           |             |             |                   |
| Management.Alarm.Create                                | X           | X           |             |                   |
| Compute.ResourceCollection.Move                        | X           | X           |             |                   |
| Management.Library.Create                              | X           | X           |             |                   |
| Compute.Storagesystem.Edit                             | X           |             |             |                   |
| Compute.Snapshot.Delete_all                            | X           |             |             |                   |
| Network.Port.Move                                      | X           |             |             |                   |
| Compute.VApp.Clone                                     | X           | X           |             |                   |
| Compute.VApp.Clone_Assign_To_Vapp                      | X           | X           |             |                   |
| Compute.VApp.Clone_Assign_To_ResourcePool              | X           | X           |             |                   |
| Management.Extension.Create                            | X           | X           |             |                   |
| Storage.Disk.View                                      | X           | X           |             |                   |
| Compute.VirtualMachine.Suspend                         | X           |             |             |                   |
| Management.Alarm.Delete                                | X           | X           |             |                   |
| Management.License.Delete                              | X           |             |             |                   |
| Management.Library.Import                              | X           | X           |             |                   |
| Compute.UpdateManager.Edit                             | X           |             |             |                   |
| Compute.VirtualMachine.View                            | X           | X           |             | X                 |
| Storage.Datastore.Manage                               | X           | X           |             |                   |
| Network.Port.View                                      | X           | X           |             | X                 |
| Network.IPPool.View                                    | X           | X           |             |                   |
| Compute.VirtualMachine.Create                          | X           | X           |             |                   |
| Compute.VirtualMachine.Create_DeviceConnection         | X           | X           |             |                   |
| Compute.VirtualMachine.Create_SetMedia                 | X           | X           |             |                   |
| Compute.VirtualMachine.Create_ChangeTracking           | X           |             |             |                   |
| Compute.VirtualMachine.Create_AdvancedConfig           | X           | X           |             |                   |
| Compute.VirtualMachine.Create_SwapPlacement            | X           | X           |             |                   |
| Compute.VirtualMachine.Create_HostUSBDevice            | X           | X           |             |                   |
| Compute.VirtualMachine.Create_RawDevice                | X           | X           |             |                   |
| Compute.VirtualMachine.Create_NetworkAssignment        | X           | X           |             |                   |
| Compute.VirtualMachine.Create_AddNewDisk               | X           | X           |             |                   |
| Compute.VirtualMachine.Create_AddExistingDisk          | X           | X           |             |                   |
| Compute.VirtualMachine.Create_Datastore                | X           | X           |             |                   |
| Compute.VirtualMachine.Create_ResourcePoolAssignment   | X           | X           |             |                   |
| Compute.Datacenter.View                                | X           | X           |             | X                 |
| Management.KeyManagementServer.Edit                    | X           |             |             |                   |
| Management.Administration.View                         | X           | X           |             | X                 |
| Management.Administration.Edit                         | X           |             |             |                   |
| Management.Key.Install                                 | X           |             |             |                   |
| Compute.VApp.Create                                    | X           |             |             |                   |
| Management.Library.Export                              | X           |             |             |                   |
| Network.Interface.Create                               | X           |             |             |                   |
| Storage.Disk.Delete                                    | X           |             |             |                   |
| Compute.Resource.Move                                  | X           |             |             |                   |
| Management.Profile.Create                              | X           |             |             |                   |
| Compute.Snapshot.Create                                | X           |             |             |                   |
| Management.Administration.Delete                       | X           |             |             |                   |
| Compute.VirtualMachine.Manage                          | X           |             |             |                   |
| Network.Port.Delete                                    | X           |             |             |                   |
| Management.License.View                                | X           |             |             |                   |
| Storage.StoragePod.Delete                              | X           |             |             |                   |
| Network.Switch.View                                    | X           |             |             | X                 |
| Compute.UpdateManager.Delete                           | X           |             |             |                   |
| Compute.Storagesystem.Create                           | X           |             |             |                   |
| Compute.VirtualMachine.Edit                            | X           |             |             |                   |
| Compute.VirtualMachine.Power_on                        | X           |             |             |                   |
| Management.Extension.Edit                              | X           |             |             |                   |
| Compute.Hostsystem.Login                               | X           |             |             |                   |
| Management.Library.Delete                              | X           |             |             |                   |
| Storage.StorageCapability.Delete                       | X           |             |             |                   |
| Compute.Hostsystem.Install                             | X           |             |             |                   |
| Compute.UpdateManager.Download                         | X           |             |             |                   |
| Compute.VirtualMachine.Delete_from_inventory           | X           |             |             |                   |
| Compute.Hostsystem.Delete                              | X           |             |             |                   |
| Management.Tag.Create                                  | X           |             |             |                   |
| Compute.ResourceCollection.Create                      | X           |             |             |                   |
| Management.Library.Sync                                | X           |             |             |                   |
| Management.Library.Add                                 | X           |             |             |                   |
| Management.Administration.Create                       | X           |             |             |                   |
| Management.Tag.Assign                                  | X           |             |             |                   |
| Storage.Datastore.Delete                               | X           |             |             |                   |
| Storage.Datastore.Edit                                 | X           |             |             |                   |
| Storage.StoragePod.Create                              | X           |             |             |                   |
| Compute.VApp.Delete                                    | X           |             |             |                   |
| Compute.VirtualMachine.Move                            | X           |             |             |                   |
| Storage.Cluster.Manage                                 | X           |             |             |                   |
| Compute.VApp.Edit                                      | X           |             |             |                   |
| Compute.UpdateManager.Create                           | X           |             |             |                   |
| Compute.VApp.Move                                      | X           |             |             |                   |
| Compute.Hostsystem.View                                | X           |             |             | X                 |
| Compute.Datastore.Assign                               | X           |             |             |                   |
| Compute.VirtualMachine.Power_off                       | X           |             |             |                   |
| Compute.VApp.Suspend                                   | X           |             |             |                   |
| Storage.Storagesystem.Assign                           | X           |             |             |                   |
| Compute.HostsystemCollection.Move                      | X           |             |             |                   |
| Management.Tag.Edit                                    | X           |             |             |                   |
| Management.Authorization.View                          | X           |             |             |                   |
| Management.Profile.View                                | X           |             |             |                   |
| Management.Key.Create                                  | X           |             |             |                   |
| Compute.VirtualMachine.Install                         | X           |             |             |                   |
| Compute.Hostsystem.Create                              | X           |             |             |                   |
| Compute.HostsystemCollection.Delete                    | X           |             |             |                   |
| Storage.Storagesystem.Create                           | X           |             |             |                   |
| Storage.Storagesystem.Delete                           | X           |             |             |                   |
| Management.Key.Delete                                  | X           |             |             |                   |
| Management.Tag.Unassign                                | X           |             |             |                   |
| Network.Port.Edit                                      | X           |             |             |                   |
| Storage.Datastore.Move                                 | X           |             |             |                   |
| Storage.Disk.Edit                                      | X           |             |             |                   |
| Compute.HostsystemCollection.View                      | X           | X           |             | X                 |
| Network.Port.Create                                    | X           |             |             |                   |
| Storage.Disk.Create                                    | X           |             |             |                   |
| Compute.VirtualMachine.Delete                          | X           | X           |             |                   |
| Compute.HostsystemCollection.Edit                      | X           | X           |             |                   |
| Storage.Disk.Move                                      | X           |             |             |                   |
| Compute.VirtualMachine.Clone                           | X           | X           |             |                   |
| Compute.VirtualMachine.Clone_NetworkAssignment         | X           | X           |             |                   |
| Compute.VirtualMachine.Clone_ResourcePoolAssignment    | X           | X           |             |                   |
| Compute.VirtualMachine.Clone_To_VirtualMachine         | X           |             |             |                   |
| Compute.VirtualMachine.Clone_To_Template               | X           |             |             |                   |
| Compute.VirtualMachine.Clone_Customization             | X           |             |             |                   |
| Compute.VirtualMachine.Clone_Datastore                 | X           | X           |             |                   |
| Storage.Datastore.Create                               | X           |             |             |                   |
| Compute.ResourcePool.Create                            | X           | X           |             |                   |
| Network.Switch.Move                                    | X           |             |             |                   |
| Compute.Datacenter.Create                              | X           |             |             |                   |
| Compute.Snapshot.Edit                                  | X           | X           |             |                   |
| Compute.ResourcePool.View                              | X           | X           |             | X                 |
| Management.Tag.Delete                                  | X           | X           |             |                   |
| Management.Certificate.Install                         | X           |             |             |                   |
| Compute.VApp.Power_on                                  | X           | X           |             |                   |
| Storage.StorageCapability.Create                       | X           |             |             |                   |
| Compute.Datacenter.Delete                              | X           |             |             |                   |
| Management.Key.View                                    | X           |             |             |                   |
| Compute.Storagesystem.Delete                           | X           |             |             |                   |
| Compute.Hostsystem.Manage                              | X           |             |             |                   |
| Management.KeyManagementServer.Register                | X           |             |             |                   |
| Compute.Hostsystem.Edit                                | X           |             |             |                   |
| Compute.ResourcePool.Edit                              | X           | X           |             |                   |
| Compute.Datastore.Unassign                             | X           | X           |             |                   |
| Compute.Hostsystem.Move                                | X           |             |             |                   |
| Compute.ResourceCollection.Edit                        | X           | X           |             |                   |
| Compute.VirtualMachine.Reboot                          | X           |             |             |                   |
| Compute.UpdateManager.Import                           | X           |             |             |                   |
| Storage.StoragePod.Edit                                | X           |             |             |                   |
| Compute.ResourcePool.Delete                            | X           | X           |             |                   |
| Network.Interface.Delete                               | X           |             |             |                   |
| Compute.ResourcePool.Move                              | X           | X           |             |                   |
| Compute.VirtualMachine.Shutdown                        | X           | X           |             |                   |
| Management.Library.View                                | X           |             |             | X                 |
| Management.Extension.Delete                            | X           | X           |             |                   |
| Network.Interface.Edit                                 | X           |             |             |                   |
| Compute.UpdateManager.Configure                        | X           |             |             |                   |
| Management.Administration.Login                        | X           | X           |             | X                 |
| Management.Certificate.Create                          | X           |             |             |                   |
| Compute.VirtualMachine.Revert                          | X           |             |             |                   |
| Management.Alarm.Edit                                  | X           | X           |             |                   |
| Storage.Storagesystem.Edit                             | X           | X           |             |                   |
| Storage.StorageCapability.Edit                         | X           |             |             |                   |
| Storage.Storagesystem.View                             | X           |             |             |                   |
| Compute.HostsystemCollection.Create                    | X           |             |             |                   |
| Compute.VirtualMachine.Migrate                         | X           | X           |             |                   |
| Compute.Datacenter.Edit                                | X           |             |             |                   |
| Management.Authorization.Edit                          | X           | X           |             |                   |
| Compute.ResourceCollection.Delete                      | X           | X           |             |                   |
| Storage.Datastore.View                                 | X           | X           |             |                   |
| Compute.Cluster.View                                   | X           | X           |             | X                 |
| Storage.Storagesystem.Revert                           | X           | X           |             |                   |
| Compute.Snapshot.Delete                                | X           |             |             |                   |
| Management.Profile.Delete                              | X           |             |             |                   |
| Management.KeyManagementServer.View                    | X           |             |             |                   |
| Compute.Datacenter.Move                                | X           |             |             |                   |
| Management.KeyManagementServer.Delete                  | X           |             |             |                   |
| Compute.VApp.Shutdown                                  | X           | X           |             |                   |
| Management.License.Edit                                | X           |             |             |                   |
| Compute.VApp.Delete_from_inventory                     | X           | X           |             |                   |
| Network.Switch.Create_LogicalPort                      | X           |             | X           |                   |
| Network.Switch.Edit_LogicalPort                        | X           |             | X           |                   |
| Network.Switch.Delete_LogicalPort                      | X           |             | X           |                   |
| CloudControl.Inventory.Delete                          | X           |             |             |                   |
| CloudControl.Applinks.View                             | X           |             |             |                   |
| CloudControl.Dashboard.Create                          | X           |             |             |                   |
| CloudControl.Color.View                                | X           |             |             |                   |
| CloudControl.Report.Delete                             | X           |             |             |                   |
| CloudControl.Eula.Read                                 | X           |             |             |                   |
| CloudControl.Applinks.Privileges                       | X           |             |             |                   |
| CloudControl.AuthenticationConfig.Create               | X           |             |             |                   |
| CloudControl.AuthenticationConfig.View                 | X           |             |             |                   |
| CloudControl.Authorization.Create                      | X           |             |             |                   |
| CloudControl.Authentication.Edit                       | X           |             |             |                   |
| CloudControl.Product.View                              | X           |             |             |                   |
| CloudControl.Vulnerability.View                        | X           |             |             |                   |
| CloudControl.Applinks.Create                           | X           |             |             |                   |
| CloudControl.Applinks.Rotate_Secret                    | X           |             |             |                   |
| CloudControl.RetentionPolicy.View                      | X           |             |             |                   |
| CloudControl.Applinks.Register                         | X           |             |             |                   |
| CloudControl.AuthenticationConfig.Edit                 | X           |             |             |                   |
| CloudControl.Asc.UserDetails                           | X           |             |             |                   |
| CloudControl.Inventory.Create                          | X           |             |             |                   |
| CloudControl.Authorization.Delete                      | X           |             |             |                   |
| CloudControl.Report.Create                             | X           |             |             |                   |
| CloudControl.Tag.ImportUnassign                        | X           |             |             |                   |
| CloudControl.Applinks.Edit                             | X           |             |             |                   |
| CloudControl.Authentication.Logout                     | X           |             |             |                   |
| CloudControl.ApplianceHealth.View                      | X           |             |             |                   |
| CloudControl.Log.Create                                | X           |             |             |                   |
| CloudControl.LogRetention.Edit                         | X           |             |             |                   |
| CloudControl.LogRetention.View                         | X           |             |             |                   |
| CloudControl.Inventory.Edit                            | X           |             |             |                   |
| CloudControl.RetentionPolicy.Edit                      | X           |             |             |                   |
| CloudControl.Applinks.Delete                           | X           |             |             |                   |
| CloudControl.CompliancePolicy.Edit                     | X           |             |             |                   |
| CloudControl.CompliancePolicy.View                     | X           |             |             |                   |
| CloudControl.Inventory.View                            | X           |             |             |                   |
| CloudControl.Collector.Edit                            | X           |             |             |                   |
| CloudControl.Tag.View                                  | X           |             |             |                   |
| CloudControl.Tag.ImportAssign                          | X           |             |             |                   |
| Management.Certificate.Edit                            | X           | X           |             |                   |
| Management.Certificate.View                            | X           |             |             |                   |
| CloudControl.Password.Edit                             | X           |             |             |                   |
| CloudControl.License.View                              | X           |             |             |                   |
| CloudControl.License.Edit                              | X           |             |             |                   |
| CloudControl.License.Delete                            | X           |             |             |                   |
| CloudControl.Tag.Create                                | X           |             |             |                   |
| CloudControl.Tag.Assign                                | X           |             |             |                   |
| CloudControl.Tag.Edit                                  | X           |             |             |                   |
| CloudControl.Authorization.View                        | X           |             |             |                   |
| CloudControl.Tag.Unassign                              | X           |             |             |                   |
| CloudControl.Tag.Delete                                | X           |             |             |                   |
| CloudControl.Authorization.Edit                        | X           |             |             |                   |
| Network.ContextProfile.Create                          | X           |             | X           |                   |
| Network.ContextProfile.Delete                          | X           |             | X           |                   |
| Network.ContextProfile.Edit                            | X           |             | X           |                   |
| Compute.VirtualMachine.Edit_Name                       | X           |             |             |                   |
| Compute.VirtualMachine.Edit_Annotation                 | X           |             |             |                   |
| Compute.VirtualMachine.Edit_DeviceConnection           | X           |             |             |                   |
| Compute.VirtualMachine.Edit_NetworkAssignment          | X           | X           |             |                   |
| Compute.VirtualMachine.Edit_AddNewDisk                 | X           | X           |             |                   |
| Compute.VirtualMachine.Edit_AddExistingDisk            | X           | X           |             |                   |
| Compute.VirtualMachine.Edit_RemoveDisk                 | X           | X           |             |                   |
| Compute.VirtualMachine.Edit_ExtendDisk                 | X           |             |             |                   |
| Compute.VirtualMachine.Edit_EditDevice                 | X           | X           |             |                   |
| Compute.VirtualMachine.Edit_AddRemoveDevice            | X           | X           |             |                   |
| Compute.VirtualMachine.Edit_SetMedia                   | X           |             |             |                   |
| Compute.VirtualMachine.Edit_HostUSBDevice              | X           | X           |             |                   |
| Compute.VirtualMachine.Edit_RawDevice                  | X           | X           |             |                   |
| Compute.VirtualMachine.Edit_CPU                        | X           | X           |             |                   |
| Compute.VirtualMachine.Edit_Memory                     | X           | X           |             |                   |
| Compute.VirtualMachine.Edit_Settings                   | X           | X           |             |                   |
| Compute.VirtualMachine.Edit_Resource                   | X           | X           |             |                   |
| Compute.VirtualMachine.Edit_AdvancedConfig             | X           |             |             |                   |
| Compute.VirtualMachine.Edit_SwapPlacement              | X           | X           |             |                   |
| Compute.VirtualMachine.Edit_ChangeTracking             | X           |             |             |                   |
| Compute.VirtualMachine.Edit_MKSControl                 | X           | X           |             |                   |
| Compute.VirtualMachine.Edit_ManagedBy                  | X           | X           |             |                   |
| Compute.VirtualMachine.Edit_PortgroupCanUse            | X           |             |             |                   |
| Compute.VirtualMachine.Edit_SwitchCanUse               | X           |             |             |                   |
| Compute.VirtualMachine.Edit_Datastore                  | X           | X           |             |                   |
| Network.Firewall.Enable_Identity                       | X           |             | X           |                   |
| Network.Firewall.Disable_Identity                      | X           |             | X           |                   |
| Network.IPAM.Create                                    | X           |             | X           |                   |
| Network.IPAM.Delete                                    | X           |             | X           |                   |
| Network.IPAM.Edit                                      | X           |             | X           |                   |
| Network.Switch.Delete_Bulk                             | X           |             | X           |                   |
| Network.SecurityGroup.Delete_Bulk                      | X           |             | X           |                   |
| Network.IPAddressGroup.Delete_Bulk                     | X           |             | X           |                   |
| Network.IPPool.Delete_Bulk                             | X           |             | X           |                   |
| Network.MacAddressGroup.Delete_Bulk                    | X           |             | X           |                   |
| Network.Switch.Delete_Bulk_LogicalPort                 | X           |             | X           |                   |
| Network.Router.Delete_Bulk                             | X           |             | X           |                   |
| Network.DHCP.Delete_Bulk                               | X           |             | X           |                   |
| Network.LoadBalancer.Delete_Bulk                       | X           |             | X           |                   |
| Network.IPAM.Delete_Bulk                               | X           |             | X           |                   |
| CloudControl.Role.Export                               | X           |             |             |                   |
| CloudControl.Role.Import                               | X           |             |             |                   |
| CloudControl.TrustManifest.Authorize_AccessControl     | X           |             |             |                   |
| CloudControl.TrustManifest.Create_AccessControl        | X           |             |             |                   |
| CloudControl.TrustManifest.Delete_AccessControl        | X           |             |             |                   |
| CloudControl.TrustManifest.Edit_AccessControl          | X           |             |             |                   |
| CloudControl.TrustManifest.Authorize_DeploymentControl | X           |             |             |                   |
| CloudControl.TrustManifest.Create_DeploymentControl    | X           |             |             |                   |
| CloudControl.TrustManifest.Delete_DeploymentControl    | X           |             |             |                   |
| CloudControl.TrustManifest.Edit_DeploymentControl      | X           |             |             |                   |
| CloudControl.TrustManifest.Authorize_SecondaryApproval | X           |             |             |                   |
| CloudControl.TrustManifest.Create_SecondaryApproval    | X           |             |             |                   |
| CloudControl.TrustManifest.Delete_SecondaryApproval    | X           |             |             |                   |
| CloudControl.TrustManifest.Edit_SecondaryApproval      | X           |             |             |                   |
| CloudControl.TrustManifest.Authorize_ExceptionControl  | X           |             |             |                   |
| CloudControl.TrustManifest.Create_ExceptionControl     | X           |             |             |                   |
| CloudControl.TrustManifest.Delete_ExceptionControl     | X           |             |             |                   |
| CloudControl.TrustManifest.Edit_ExceptionControl       | X           |             |             |                   |
| Network.Switch.Edit_Policy                             | X           |             |             |                   |
| Network.Switch.Edit_PortSetting                        | X           |             |             |                   |
| Network.Switch.Edit_PortMirroring                      | X           |             |             |                   |
| Network.Switch.Edit_ResourceManagement                 | X           |             |             |                   |
| Management.Client.Internal                             | X           |             |             |                   |
| Management.Integrations.Manage                         | X           |             |             |                   |
| Compute.VirtualMachine.StorageProfile                  | X           |             |             |                   |
| Compute.Snapshot.Create_WithMemory                     | X           |             |             |                   |
| Network.Port.Edit_Policy                               | X           |             |             |                   |
| Compute.VirtualMachine.Migrate_ResourcePoolAssignment  | X           |             |             |                   |
| Compute.VirtualMachine.Migrate_CreateNewVM             | X           |             |             |                   |
| Compute.VirtualMachine.Migrate_HotMigrate              | X           |             |             |                   |
| Compute.VirtualMachine.Migrate_Datastore               | X           |             |             |                   |
| Compute.VirtualMachine.Migrate_NetworkAssignment       | X           |             |             |                   |
| CloudControl.IdentityProvider.Configure                | X           |             |             |                   |
| Network.TransportZone.Create                           | X           |             |             |                   |
| Network.TransportZone.Edit                             | X           |             |             |                   |
| Network.TransportZone.Delete                           | X           |             |             |                   |
| Network.TransportZone.Delete_Bulk                      | X           |             |             |                   |
| Network.VPN.Create                                     | X           |             |             |                   |
| Network.VPN.Delete                                     | X           |             |             |                   |
| Network.VPN.Edit                                       | X           |             |             |                   |
{: caption="Table 1. HTCC roles" caption-side="top"}

**Next topic**: [Operational tooling identity and access management](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-iam-vrealize)

## Related links
{: #vrw-iam-hytrust-related}

* [IBM Cloud compliance programs](https://www.ibm.com/cloud/compliance)
* [HyTrust CloudControl](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_considerations)
* [HyTrust DataControl](/docs/vmwaresolutions?topic=vmwaresolutions-htdc_considerations)
* [IBM Cloud Hyper Protect Crypto Services API](https://cloud.ibm.com/apidocs/hs-crypto)
