//READ ME!
//What you first have to do is go to our ItemRenderer class and replace the code in it with the code below.

public void renderItemInFirstPerson(float p_78440_1_)
    {
        float var2 = 1.0F - (this.prevEquippedProgress + (this.equippedProgress - this.prevEquippedProgress) * p_78440_1_);
        EntityPlayerSP var3 = this.mc.thePlayer;
        float var4 = var3.getSwingProgress(p_78440_1_);
        float var5 = var3.prevRotationPitch + (var3.rotationPitch - var3.prevRotationPitch) * p_78440_1_;
        float var6 = var3.prevRotationYaw + (var3.rotationYaw - var3.prevRotationYaw) * p_78440_1_;
        this.func_178101_a(var5, var6);
        this.func_178109_a(var3);
        this.func_178110_a((EntityPlayerSP)var3, p_78440_1_);
        GlStateManager.enableRescaleNormal();
        GlStateManager.pushMatrix();

        if (this.itemToRender != null)
        {
            if (this.itemToRender.getItem() == Items.filled_map)
            {
                this.func_178097_a(var3, var5, var2, var4);
            }
            else if (var3.getItemInUseCount() > 0)
            {
                EnumAction var7 = this.itemToRender.getItemUseAction();

                switch (ItemRenderer.SwitchEnumAction.field_178094_a[var7.ordinal()])
                {
                    case 1:
                        this.func_178096_b(var2, 0.0f);
                        break;

                    case 2:
                    case 3:
                        this.func_178104_a(var3, p_78440_1_);
                        this.func_178096_b(var2, 0.0f); // replace 0.0f -> var4
                        break;

                    case 4:
                        this.func_178096_b(var2, 0.0f); // replace 0.0f -> var4
                        this.func_178103_d();
                        break;

                    case 5:
                        this.func_178096_b(var2, 0.0f); // replace 0.0f -> var4
                        this.func_178098_a(p_78440_1_, var3);
                }
            }
            else
            {
                this.func_178105_d(var4);
                this.func_178096_b(var2, var4);
            }

            this.renderItem(var3, this.itemToRender, ItemCameraTransforms.TransformType.FIRST_PERSON);
        }
        else if (!var3.isInvisible())
        {
            this.func_178095_a(var3, var2, var4);
        }

        GlStateManager.popMatrix();
        GlStateManager.disableRescaleNormal();
        RenderHelper.disableStandardItemLighting();
    }
    
    //after that go to the Minecraft.java class and find, if (this.leftClickCounter <= 0 && !this.thePlayer.isUsingItem()) and replace it with  if (!this.thePlayer.isUsingItem());
