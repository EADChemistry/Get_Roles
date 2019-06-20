# Get_Roles
Get list of members that have a role
@bot.command(pass_context=True)  
async def getuser(ctx,*args):
  server = ctx.message.server
  role_name = (' '.join(args))
  role_id = server.roles[0]
  for role in server.roles:
    if role_name == role.name:
      role_id = role
      break
  else:
    await bot.say("Role doesn't exist")
    return    
  for member in server.members:
    if role_id in member.roles:
      await bot.say(f"{role_name} - {member.name}")
