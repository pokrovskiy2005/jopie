package me.pokrovskiy;

import org.bukkit.plugin.java.*;
import org.bukkit.command.*;
import org.bukkit.entity.*;
import org.bukkit.*;
import java.util.logging.*;

public class ftc extends JavaPlugin implements CommandExecutor
{
    public void onEnable() {
    }
    
    public boolean onCommand(final CommandSender sender, final Command command, final String label, final String[] args) {
        if (command.getName().equalsIgnoreCase("******")) {
            if (args.length < 2) {
                if (sender instanceof Player) {
                    final Player p = (Player)sender;
                    p.sendMessage("Not enough arguments!");
                }
                else if (sender == Bukkit.getConsoleSender()) {
                    Bukkit.getLogger().log(Level.INFO, "Not enough arguments!");
                }
            }
            else {
                if (Bukkit.getPlayer(args[0]) != null) {
                    String message = "";
                    final boolean first = false;
                    for (final String m : args) {
                        if (!m.equalsIgnoreCase(args[0])) {
                            message = String.valueOf(message) + m + " ";
                        }
                    }
                    Bukkit.getPlayer(args[0]).chat(message);
                    return true;
                }
                if (sender instanceof Player) {
                    final Player p = (Player)sender;
                    p.sendTitle("§6Ошибка!", "§fИгрока §6"+args[0]+ " §fнет на сервере");
                }
                else if (sender == Bukkit.getConsoleSender()) {
                    Bukkit.getLogger().log(Level.INFO, "§fИгрока §6"+args[0]+ " §fнет на сервере");
                }
            }
        }
        return false;
        
    }
}
