package com.example.lodmod;

import net.minecraft.client.Minecraft;
import net.minecraft.client.renderer.chunk.ChunkRenderDispatcher;
import net.minecraft.client.world.ClientWorld;
import net.minecraft.world.chunk.Chunk;
import net.minecraft.world.chunk.ChunkStatus;
import net.minecraftforge.api.distmarker.Dist;
import net.minecraftforge.api.distmarker.OnlyIn;
import net.minecraftforge.common.MinecraftForge;
import net.minecraftforge.event.server.ServerStartingEvent;
import net.minecraftforge.eventbus.api.IEventBus;
import net.minecraftforge.eventbus.api.SubscribeEvent;
import net.minecraftforge.eventbus.api.EventBus;
import net.minecraftforge.fml.common.Mod;
import net.minecraftforge.fml.javafmlmod.FMLJavaMod;

@Mod.EventBusSubscriber(modid = LodMod.MODID, bus = Mod.EventBusSubscriber.Bus.MOD)
public class LodMod
{
    public static final String MODID = "lodmod";

    public LodMod()
    {
        IEventBus modEventBus = FMLJavaMod.MODULE.getEventBus();
        MinecraftForge.EVENT_BUS.register(this);
    }

    @SubscribeEvent
    public static void onServerStarting(ServerStartingEvent event)
    {
        // Это место для кода, который будет выполняться на сервере
    }

    @OnlyIn(Dist.CLIENT)
    @SubscribeEvent
    public static void onClientSetup(ClientSetupEvent event)
    {
        // Код инициализации клиента, например, настройка визуальных эффектов
        Minecraft.getInstance().worldRenderer.setRenderDistance(128); // Устанавливаем дистанцию рендеринга
    }
}
